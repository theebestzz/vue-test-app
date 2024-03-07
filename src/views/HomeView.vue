<template>
  <ul>
    <li v-for="todo in todos" :key="todo.id">{{ todo.title }}</li>
  </ul>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

interface Todo {
  id: number;
  title: string;
}

const todos = ref<Todo[]>([]);

onMounted(async () => {
  const response = await fetch("https://jsonplaceholder.typicode.com/todos/");
  todos.value = await response.json();
});
</script>