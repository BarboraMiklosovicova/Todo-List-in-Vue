<script setup lang="ts">
import ShowTodo from "./components/ShowTodo.vue";
import { Todo } from "./models/Todo";
</script>

<template>
  <ShowTodo></ShowTodo>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
