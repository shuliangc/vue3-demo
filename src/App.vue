<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="h-full flex flex-col">
    <header class="flex items-center px-4 h-14">
      <nav class="flex gap-1">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/todo">Todo</RouterLink>
      </nav>
    </header>
    <main class="h-full flex">
      <aside class="w-60 min-h-full bg-white">
        <header class="flex items-center px-4 h-10">
          Header
        </header>
      </aside>
      <main class="flex-1 h-full py-4 px-6 bg-gray-100">
        <RouterView />
      </main>
    </main>
  </div>
</template>
