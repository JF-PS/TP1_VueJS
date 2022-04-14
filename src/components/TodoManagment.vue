<template>
  <div class="hello">
    <h1 id="title">{{ title }}</h1>
    <TodoField
      v-if="!updateTodo"
      :managers="managers"
      :currentTodo="defaultTodo"
      @onAddTodo="addTodo"
    />
    <TodoField
      v-else
      :managers="managers"
      :currentTodo="updateTodo"
      @onAddTodo="addTodo"
    />
    <br />
    <TodoList :list="list" />
  </div>
</template>

<script>
import TodoField from "./TodoField.vue";
import TodoList from "./TodoList.vue";

export default {
  name: "TodoManagment",
  components: {
    TodoField,
    TodoList,
  },
  props: {
    title: String,
  },
  methods: {
    addTodo: function (newTodo) {
      const { manager, hours: currentHours } = newTodo;
      const todoManager = this.list.filter((todo) => todo.manager === manager);
      let nbHours = currentHours;
      todoManager.map((todo) => {
        const { hours } = todo;
        console.log(hours);
        nbHours = nbHours + hours;
        return todo;
      });

      if (todoManager.length <= 2 && nbHours <= 10) this.list.push(newTodo);
      else {
        if (nbHours <= 10) alert(`${manager} ne peux pas dépasser 10 h`);
        else
          alert(`${manager} ne peux pas être assigner à plus de trois tâches.`);
      }
    },
  },
  data() {
    return {
      managers: ["Morgane", "Mathias", "Momo"],
      defaultTodo: { task: "", hours: 1, manager: "Morgane" },
      updateTodo: { task: "default", hours: 1, manager: "Morgane" },
      list: [],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#title {
  font-family: "Work Sans";
  font-style: normal;
  font-weight: 700;
  font-size: 24px;
  line-height: 100%;
  /* identical to box height, or 24px */

  color: #000000;
}
</style>
