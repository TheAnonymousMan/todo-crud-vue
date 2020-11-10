<template>
  <div>
    <div>
      <h1>Todos</h1>
      <div class="legend">
        <span>Click the check mark to mark as complete</span>
        <span> <span class="incomplete-box"></span> = Incomplete </span>
        <span> <span class="complete-box"></span> = Complete </span>
      </div>
      <div
        :key="todo.id"
        v-for="todo in allTodos"
        class="todo"
        v-bind:class="{ 'is-complete': todo.completed }"
      >
        {{ todo.title }}
        <i class="far fa-check-circle" v-on:click="onCheckClick(todo)"></i>{{" "}}
        <i class="fas fa-trash-alt" v-on:click="deleteTodo(todo.id)"></i>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  name: "Todos",
  methods: {
    ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
    onCheckClick(todo) {
      const updatedTodo = {
        id: todo.id,
        title: todo.title,
        completed: !todo.completed,
      };
      this.updateTodo(updatedTodo);
    },
  },
  computed: mapGetters(["allTodos"]),
  created() {
    this.fetchTodos();
  },
};
</script>

<style scoped>
.todos {
  display: flex;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1rem;
}
.todo {
  border: 1px solid #ccc;
  background: #41b883;
  padding: 1rem;
  border-radius: 5px;
  text-align: center;
  position: relative;
  cursor: pointer;
}
i {
  /* position: absolute; */
  bottom: 10px;
  right: 10px;
  color: #fff;
  cursor: pointer;
}
.legend {
  display: flex;
  justify-content: space-around;
  margin-bottom: 1rem;
}
.complete-box,
.incomplete-box {
  display: inline-block;
  width: 10px;
  height: 10px;
}
.complete-box {
  background: #35495e;
}
.incomplete-box {
  background: #41b883;
}
.is-complete {
  color: #fff;
  background: #35495e;
}
@media (max-width: 500px) {
  .todos {
    grid-template-columns: 1fr;
  }
}
</style>
