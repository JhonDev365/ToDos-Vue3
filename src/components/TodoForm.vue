<script setup>
import { inject, ref } from "vue";

const todos = inject("todos");
const addForm = () => {
  if (text.value === "") {
    console.log("esta vacio");
    return;
  }
  //   console.log(text.value);
  const todo = {
    text: text.value,
    state: false,
    id: Date.now(),
  };
  todos.value.push(todo);
  text.value = "";
  //   console.log(todo);
  //   console.log(todos.value);
};
const text = ref("");
</script>

<template>
  <form @submit.prevent="addForm">
    <input type="text" placeholder="Ingresar tarea" v-model.trim="text" />
  </form>
</template>

<style scoped></style>
