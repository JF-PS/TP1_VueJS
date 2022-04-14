<template>
  <div>
    <h1 id="title">My Current List :</h1>

    <ul v-for="todo in list" :key="todo">
      <li>
        <div id="container">
          <div>{{ todo.task }}</div>
          <div>{{ todo.hours }}</div>
          <div>{{ todo.manager }}</div>
          <div><button class="button">Update</button></div>
          <div><button class="button">Delete</button></div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    list: Array,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#container {
  display: flex;
  justify-content: center;
  flex-direction: row;
  margin: auto;
  border-radius: 8px;
  padding: 32px;
  width: 610px;
  left: 40px;
  top: 40px;
  background: #f4f4f4;
}

#title {
  font-family: "Work Sans";
  font-style: normal;
  font-weight: 700;
  font-size: 20px;
  line-height: 100%;
  color: #000000;
}
</style>
