<script setup lang="ts">
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
const showRoutes = ref(false)
</script>

<template>
  <div class="h-full flex flex-col">
    <RouterView />
    <!-- <div
      class="fixed right-4 bottom-4 bg-black rounded-full h-8 w-8 flex items-center justify-center cursor-pointer"
    >
      导航
      <nav class="absolute bottom-8 bg-black flex flex-col gap-2" v-if="showRoutes">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/todo">Todo</RouterLink>
      </nav>
    </div> -->
  </div>
</template>
