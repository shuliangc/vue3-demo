<template>
  <div class="flex flex-col h-full">
    <ul class="flex-1 flex flex-col gap-2">
      <li
        v-for="item in todoList"
        :key="item.id"
        class="flex items-center h-8 rounded bg-white py-2 px-4"
      >
        <input type="checkbox" v-model="item.completed" />
        <span class="flex-1 mx-2" :class="{ 'line-through': item.completed }">{{
          item.content
        }}</span>
        <span class="text-lg cursor-pointer" @click="deleteTodo(item.id)">×</span>
      </li>
    </ul>
    <input
      class="border-none outline-none h-8 rounded bg-white py-2 px-4"
      type="text"
      placeholder="添加待办"
      required
      @keyup.enter="addTodo"
    />
  </div>
</template>

<script setup lang="ts" name="TodoList">
export interface TodoItem {
  id: number
  content: string
  completed: boolean
}
import { ref } from 'vue'
const todoList = ref<TodoItem[]>([])
const addTodo = (event: Event) => {
  const target = event.target as HTMLInputElement
  todoList.value.push({
    id: Math.random() * 10000,
    content: target.value,
    completed: false
  })
  target.value = ''
}
const deleteTodo = (id: number): void => {
  const index = todoList.value.findIndex((todo) => todo.id === id)
  todoList.value.splice(index, 1)
}
</script>
