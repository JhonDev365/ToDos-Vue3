<script setup>
import { inject, defineProps } from "vue";

const todos = inject("todos");

const deleteTodo = (id) => {
  todos.value = todos.value.filter((item) => item.id !== id);
};

const completed = (id) => {
  todos.value = todos.value.map((item) => {
    if (item.id === id) {
      item.state = true;
    }
    return item;
  });
};

const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <li class="items">
    <span
      role="button"
      @click="completed(todo.id)"
      :class="{ tachado: todo.state }"
      >{{ todo.text }}
    </span>
    <!-- <span role="button" @="deleteTodo(id)">X</span> -->
    <span role="button" @click="deleteTodo(todo.id)">X</span>
  </li>
</template>

<style scoped>
.items {
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
}
.tachado {
  text-decoration: line-through;
}
</style>
