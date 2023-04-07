<template>
  <main class="flex h-full">
    <aside class="w-60 min-h-full">
      <header class="flex items-center px-4 h-10">Header</header>
    </aside>
    <main class="flex-1 h-full px-6 flex flex-col" :style="{ 'background-color': '#6474bd' }">
      <TodoList />
    </main>
  </main>
</template>

<script setup lang="ts" name="TodoList">
import TodoList from './components/TodoList.vue'
</script>
