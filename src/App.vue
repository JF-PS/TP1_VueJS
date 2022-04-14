<template><TodoManagment :title="title" :managers="managers" /></template>

<script>
import TodoManagment from "./components/TodoManagment.vue";

export default {
  name: "App",
  components: {
    TodoManagment,
  },
  data() {
    return {
      title: "My TodoList : ",
    };
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
