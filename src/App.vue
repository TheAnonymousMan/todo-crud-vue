<template>
  <div id="app">
    <AddToDo />
    <Todos />
  </div>
</template>

<script>
import AddToDo from "./components/AddToDo.vue";
import Todos from "./components/Todos.vue";

export default {
  name: "App",
  components: {
    AddToDo,
    Todos,
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
