<template>
  <div>
    <img alt="Vue logo" src="./assets/shdrdc.png" width="200" height="200" />
    <HelloWorld msg="这是标题" />
  </div>
  <el-menu
    :default-active="activeIndex"
    class="el-menu-demo"
    mode="horizontal"
    @select="handleSelect"
  >
    <el-menu-item index="1">课题申报</el-menu-item>
    <el-menu-item index="2">奖励申报</el-menu-item>
  </el-menu>

  <ProjectTable v-if="activeIndex === '1'" />
  <AwardTable class="main" v-if="activeIndex === '2'" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import ProjectTable from "./components/ProjectTable.vue";
import AwardTable from "./components/AwardTable.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    ProjectTable,
    AwardTable,
  },
  data() {
    return {
      activeIndex: "1",
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
      console.log(key);
      this.activeIndex = key;
    },
  },
};
</script>

<style>
.txtCenter {
  text-align: center;
}

.main {
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
