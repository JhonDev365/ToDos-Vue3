<script setup>
import { computed, inject } from "vue";

const todos = inject("todos");
const contarActivos = computed(() => {
  return todos.value.filter((item) => item.state === false).length;
});
const deleteCompleted = () => {
  todos.value = todos.value.filter((item) => item.state === false);
};
</script>

<template>
  <li class="items">
    <span role="button">{{ contarActivos }} Activos </span>
    <span role="button" @click="deleteCompleted">Eliminar completados</span>
  </li>
</template>

<style scoped>
.items {
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
}
</style>
