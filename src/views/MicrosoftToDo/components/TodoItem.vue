<template>
  <div class="flex items-center justify-between gap-2 h-10 rounded py-2 px-4 bg-white">
    <CustomCheckbox v-model="completed">
      <template v-slot:true>
        <font-awesome-icon :icon="['fas', 'fa-circle-check']" color="#6676bf" />
      </template>
      <template v-slot:false>
        <font-awesome-icon :icon="['far', 'fa-circle']" color="#767678" />
      </template>
    </CustomCheckbox>
    <span class="flex-1" :class="{ 'line-through': props.completed }">
      {{ props.content }}
    </span>
    <CustomCheckbox v-model="stared">
      <template v-slot:true>
        <font-awesome-icon :icon="['fas', 'fa-star']" color="#6676bf" />
      </template>
      <template v-slot:false>
        <font-awesome-icon :icon="['far', 'fa-star']" color="#767678" />
      </template>
    </CustomCheckbox>
  </div>
</template>

<script setup lang="ts">
export interface ITodoItem {
  id: string
  content: string
  completed: boolean
  stared: boolean
}
import { computed } from 'vue'
import CustomCheckbox from '@/components/CustomCheckbox.vue'
const props = withDefaults(defineProps<ITodoItem>(), {
  id: '',
  content: '',
  completed: false,
  stared: true
})
const emit = defineEmits<{
  (e: 'update:completed', completed: boolean): void
  (e: 'update:stared', stared: boolean): void
}>()

const completed = computed({
  get() {
    return props.completed
  },
  set(value) {
    emit('update:completed', value)
  }
})
const stared = computed({
  get() {
    return props.stared
  },
  set(value) {
    emit('update:stared', value)
  }
})
</script>
