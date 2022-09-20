<script setup>
import { inject } from 'vue';
const estado = inject('estado');
const filtrar = valor => {
  estado.value = valor;
};
</script>

<template>
  <li class="items">
    <span role="button" @click="filtrar('active')">Activos</span>
    <span role="button" @click="filtrar('all')">All</span>
    <span role="button" @click="filtrar('complete')">Completados</span>
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
