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
  </div>

  <br />
  <div class="btn-container">
    <button id="delete-btn" @click="() => $emit('removeTodo', todo)">
      Delete
    </button>
  </div>
</template>
<style>
.done {
  text-decoration: line-through;
}

#delete-btn {
  height: 25px;
  font-size: 10px;
  width: 100px;
  justify-content: right;
}
</style>
