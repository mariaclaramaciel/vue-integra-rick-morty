<template>
  <div class="hello">
    <h2>Projeto de Integração</h2>
    <p>Fazendo requisições HTTP(get) com Axios</p>

    <input type="text" placeholder="Pesquisar Personagem" v-model="search" />
    <div class="container">
      <div v-for="character in filterSearch" :key="character.id" class="card">
        <h3 class="title">{{ character.name }}</h3>
        <div class="specifications">
          <div class="specifications-card">
            <p class="specifications-title"><strong>Espécie:</strong></p>
            <p class="specifications-sub">{{ character.species }}</p>
          </div>
          <div class="specifications-card">
            <p class="specifications-title"><strong>Gênero:</strong></p>
            <p class="specifications-sub">{{ character.gender }}</p>
          </div>
        </div>
        <img :src="character.image" alt="imagem do personagem" />
      </div>
    </div>
  </div>
</template>

<script>
import api from "@/services/api.js";

export default {
  name: "HomePage",

  data() {
    return {
      search: "",
      characters: [],
    };
  },

  mounted() {
    api.get("/character").then((response) => {
      this.characters = response.data.results;
      console.log(response.data.results);
    });
  },

  computed: {
    filterSearch() {
      return this.characters.filter((character) => {
        return character.name.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-content: center;
  margin-top: 30px;
}
.card {
  margin: 15px;
}

input {
  text-align: center;
  background: #002128;
  outline: none;
  border: 0;
  width: 250px;
  margin: 1rem;
  padding: 1rem;
  color: white;
  font-weight: 700;
  border-radius: 1rem;
}

.title {
  font-size: 25px;
}

.specifications {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.specifications-card {
  display: flex;
  justify-content: center;
  border: 2px solid #002128;
  margin: 4px;
  border-radius: 1rem;
  width: 150px;
}
.specifications-title {
  color: #14b3ca;
  margin-right: 8px;
}
.specifications-sub {
  color: #c4d45c;
}
</style>
