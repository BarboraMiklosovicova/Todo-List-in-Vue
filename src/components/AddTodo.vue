<script setup lang="ts">
import { onMounted, ref, watch } from "vue";

const description = ref("");
defineEmits(["addTodo"]);
const date = ref("");

watch(date, (newVal) => {
  localStorage.setItem("date", newVal);
});
onMounted(() => {
  date.value = localStorage.getItem("date") || "";
});
</script>
<template>
  <div class="header-container">
    <h2>
      My Todo List -
      <input
        class="date-input"
        type="text"
        placeholder="Day, Datum"
        v-model="date"
      />
    </h2>
  </div>
  <div class="create-todo">
    <h3>CREATE TODO</h3>
    <form @submit.prevent="() => $emit('addingNewTodo', description)">
      <p>What's on your todo list?</p>
      <input
        class="input-content"
        type="text"
        placeholder="add task"
        v-model="description"
      />
    </form>
  </div>
</template>
<style>
body {
  background-color: #c8e1cc;
}
.date-input {
  appearance: none;
  border: none;
  outline: none;
  background: none;
  cursor: initial;
  font-size: 15px;
  color: palevioletred;
}
.header-container {
  display: flex;
}
h2 {
  font-size: 20px;
}
.input-content {
  width: 80vw;
  height: 30px;
}
</style>
