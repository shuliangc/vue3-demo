<template>
  <div class="flex flex-col justify-between h-full pb-3">
    <div class="h-20 flex items-center justify-between">
      <span class="text-2xl font-bold text-white">2023 春节回家打包行李</span>
      <span
        class="text-white px-3 py-0.5 rounded cursor-pointer"
        :style="{ 'background-color': '#5766a9' }"
      >
        <font-awesome-icon :icon="['fas', 'ellipsis']" />
      </span>
    </div>
    <div class="flex-1">
      <TodoItem />
    </div>
    <TodoInput />
  </div>
</template>

<script setup lang="ts">
import TodoInput from './TodoInput.vue'
import TodoItem from './TodoItem.vue'
</script>

<style scoped></style>
