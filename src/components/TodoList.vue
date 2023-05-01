<script setup lang="ts">
import { ref } from "vue";
import { Todo } from "../models/Todo";
import AddTodo from "../components/AddTodo.vue";
import ShowTodo from "./ShowTodo.vue";

const todos = ref<Todo[]>(JSON.parse(localStorage.getItem("todos") || "[]"));

const addTodo = (description: string) => {
  todos.value.push(new Todo(description, false));
  saveToLs(todos.value);
  console.log("Added");
};
function saveToLs(tasks: Todo[]) {
  localStorage.setItem("todos", JSON.stringify(tasks));
}
const handleToggle = (i: number) => {
  todos.value[i].done = !todos.value[i].done;
  saveToLs(todos.value);
};
const removeTodo = (i: number) => {
  todos.value.splice(i, 1);
  saveToLs(todos.value);
};
</script>
<template>
  <div>
    <AddTodo @addingNewTodo="addTodo"></AddTodo>

    <div class="todos">
      <ShowTodo
        :todo="todo"
        v-for="(todo, index) in todos"
        @toggleTodo="() => handleToggle(index)"
        @removeTodo="() => removeTodo(index)"
        :key="index"
      >
      </ShowTodo>
    </div>
  </div>
</template>
<style>
ul {
  list-style: none;
}
.todos {
  margin-top: 20px;
  font-size: 18px;
  width: 300px;
  height: 40px;

  background-color: transparent;
}

input {
  border: none;
}
</style>
