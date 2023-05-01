<script setup lang="ts">
import { Todo } from "../models/Todo";

interface IShowTodoProps {
  todo: Todo;
}
defineProps<IShowTodoProps>();
defineEmits(["toggleTodo", "removeTodo"]);
</script>
<template>
  <div class="todo">
    <input type="checkbox" :checked="todo.done" @change="$emit('toggleTodo')" />
    <span :class="{ done: todo.done }"> {{ todo.description }} </span>
    <button @click="() => $emit('removeTodo', todo)">Delete</button>
  </div>
</template>
<style>
.todo {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 10px;
  margin-bottom: 10px;
  background-color: #f9f9f9;
}

.done {
  text-decoration: line-through;
}
</style>
