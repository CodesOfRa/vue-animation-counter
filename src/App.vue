<template>
  <div class="header">
    <img alt="Vue logo" src="./assets/logo.png" />
    <span>Weekly downloads</span>
  </div>
  <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  align-items: center;
}
.header {
  display: flex;
  justify-content: center;
  align-items: center;
}
.header span {
  font-size: 2rem;
}
</style>
