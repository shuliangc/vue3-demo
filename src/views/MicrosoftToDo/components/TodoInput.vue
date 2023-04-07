<template>
  <div class="flex items-center rounded h-11 text-white" :style="{ background: '#5765a7' }">
    <span class="px-4"><font-awesome-icon :icon="['fas', 'plus']" /></span>
    <input
      class="flex-1 border-none outline-none dark:bg-inherit bg-inherit"
      type="text"
      placeholder="添加待办"
      required
    />
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
input[type='text']::placeholder {
  color: #fff;
  font-size: 14px;
  font-weight: bold;
}
</style>
