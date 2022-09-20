<script setup>
import { provide, ref, watchEffect } from 'vue';
import TodoForm from './TodoForm.vue';
import TodoList from './TodoList.vue';
const todos = ref([]);
provide('todos', todos);
// Local storage, persistencia de los datos
if (localStorage.getItem('todos')) {
  todos.value = JSON.parse(localStorage.getItem('todos'));
}

watchEffect(() => {
  // console.log(todos.value.length);
  // console.log(todos.value);
  localStorage.setItem('todos', JSON.stringify(todos.value));
});
</script>

<template>
  <h1>ToDos</h1>
  <TodoForm />
  <TodoList />
</template>

<style scoped></style>
