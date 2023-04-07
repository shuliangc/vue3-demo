<template>
  <span>
    <input type="checkbox" class="hidden" :id="randomId" v-model="value" />
    <label :for="randomId">
      <slot name="true" v-if="value" />
      <slot name="false" v-else />
    </label>
  </span>
</template>

<script setup lang="ts">
export interface ICustomCheckbox {
  modelValue: boolean
  disabled?: boolean
}
import { computed } from 'vue'
const props = defineProps<ICustomCheckbox>()
const emit = defineEmits<{
  (e: 'update:modelValue', modelValue: boolean): void
}>()
const randomId = String(Math.random() * 10000)
const value = computed({
  get() {
    return props.modelValue
  },
  set(value) {
    emit('update:modelValue', value)
  }
})
</script>
