<template>
  <div class="flex items-center h-42 rounded py-2 px-4">
    <input type="checkbox" :value="props.completed" />
    <span class="flex-1 mx-2" :class="{ 'line-through': props.completed }">
      <template>
        {{ props.content }}
      </template>
    </span>
    <span class="text-lg cursor-pointer" @click="emit('on-delete', props.id)">⭐️</span>
  </div>
</template>

<script setup lang="ts">
export interface TodoItem {
  id: string
  content: string
  completed: boolean
  stared: boolean
}
const props = withDefaults(defineProps<TodoItem>(), {
  id: '',
  content: '',
  completed: false,
  stared: false
})

const emit = defineEmits<{
  (e: 'on-delete', id: string): void
  (e: 'on-complete', id: string): void
}>()
</script>

<style scoped></style>
