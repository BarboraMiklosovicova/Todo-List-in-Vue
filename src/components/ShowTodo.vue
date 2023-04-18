<script setup lang="ts">
import { Todo } from "../models/Todo";

interface IShowTodo {
  todo: Todo;
}

defineProps<IShowTodo>(); // ta emot todo från parent
</script>

<template>
  <input type="text" placeholder="Add task" />
  <button>Add</button>
</template>

<style scoped></style>
