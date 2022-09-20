<script setup>
import { computed, inject, provide, ref } from 'vue';
import TodoItem from './TodoItem.vue';
import TodoFooter from './TodoFooter.vue';
import TodoFiltro from './TodoFiltro.vue';
// const todos = inject('todos');
// modificacoms esta referencia para inyectarle en filtro y poder realizar lso filtros
const todosTodos = inject('todos');
const estado = ref('all');
const todos = computed(() => {
  if (estado.value === 'all') {
    return todosTodos.value;
  }
  if (estado.value === 'active') {
    return todosTodos.value.filter(item => item.state === false);
  }
  if (estado.value === 'complete') {
    return todosTodos.value.filter(item => item.state === true);
  }
});
provide('estado', estado);
</script>

<template>
  <ul>
    <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" />
    <li v-if="todos.length === 0">No hay ToDos...</li>
    <TodoFooter v-if="todos.length !== 0" />
    <TodoFiltro />
  </ul>
</template>

<style scoped></style>
