<template>
  <img alt="Vue logo" src="./assets/shdrdc.png" width="200" height="200" />
  <HelloWorld msg="Welcome to Project Information Platform" />
  <ProjectTable />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import ProjectTable from "./components/ProjectTable.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    ProjectTable,
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
}
</style>
