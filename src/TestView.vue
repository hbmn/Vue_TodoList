<script setup>
import { reactive, ref } from "vue";

const state = reactive({
  todo: "",
  todos: [],
});
const addTodo = () => {
  state.todos.push(state.todo);
  state.todo = "";
};
const removeTodo = (index) => state.todos.splice(index, 1);

const color = ref("mediumblue");
</script>

<template>
  <div id="app">
    <h1>Todoリスト</h1>
    <input v-model="state.todo" /><br />
    <button @click="addTodo">追加</button>
    <ul>
      <li v-for="(todo, index) in state.todos" :key="todo">
        <span>{{ index + 1 }}</span
        >{{ todo }}
        <span v-bind:style="{ color: color }" @click="removeTodo(index)"
          >×</span
        >
      </li>
    </ul>
  </div>
</template>

<style scoped>
#app {
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
}
h1 {
  color: darkorchid;

  letter-spacing: 0.1rem;
  font-size: 32px;
}
button {
  margin-top: 20px;
  background-color: #888;
  border: none;
  color: #fff;
  padding: 5px 10px;
  border-radius: 3px;
}
ul {
  display: block;
  text-align: center;
  padding: 0 80px;
}
li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
  border-bottom: 1px solid #f6f6f6;
  padding-bottom: 5px;
}
li span {
  margin: 0 10px;
}
</style>
