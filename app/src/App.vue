<template>
  <div class="container">
    <MainComponent />
  </div>
</template>

<script>
import MainComponent from "./components/Main.vue";

export default {
  name: "App",
  components: {
    MainComponent,
  },
};
</script>

<style lang="scss" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.container {
  margin: 60px auto 52px 45px;
}
</style>
