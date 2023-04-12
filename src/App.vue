<template>
  <img alt="Vue logo" src="./assets/logo.png" class="logo" />
  <HomePage />
</template>

<script>
import HomePage from "./components/Home.vue";

export default {
  name: "App",
  components: {
    HomePage,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.logo {
  height: 150px;
}
</style>
