<template>
  <div class="all-tasks">
    <AllTasks></AllTasks>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import AllTasks from "./components/AllTasks.vue";

export default {
  name: "App",
  components: {
    AllTasks,
  },
};
</script>

<style>
@import './assets/style.scss';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  /* -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}
</style>
