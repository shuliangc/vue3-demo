<template>
  <main class="flex h-full">
    <aside class="w-60 min-h-full">
      <header class="flex items-center px-4 h-10">Header</header>
    </aside>
    <main class="flex-1 h-full px-6 flex flex-col">
      <header class="h-14 flex items-center text-lg">title</header>
      <main class="h-full flex flex-col justify-between">
        <ul class="flex-1 flex flex-col gap-2">
          <li
            v-for="item in todoList"
            :key="item.id"
            class="flex items-center h-8 rounded py-2 px-4"
          >
            <input type="checkbox" v-model="item.completed" />
            <span class="flex-1 mx-2" :class="{ 'line-through': item.completed }">
              <template>
                {{ item.content }}
              </template>
            </span>
            <span class="text-lg cursor-pointer" @click="deleteTodo(item.id)">×</span>
          </li>
        </ul>
        <input
          class="border-none outline-none h-8 rounded py-2 px-4 mb-2 dark:bg-inherit"
          type="text"
          placeholder="添加待办"
          required
          @keyup.enter="addTodo"
        />
      </main>
    </main>
  </main>
</template>

<script setup lang="ts" name="TodoList">
export interface TodoItem {
  id: number
  content: string
  completed: boolean
}
import { ref } from 'vue'
const todoList = ref<TodoItem[]>([])
// 新增待办
const addTodo = (event: Event) => {
  const target = event.target as HTMLInputElement
  todoList.value.push({
    id: Math.random() * 10000,
    content: target.value,
    completed: false
  })
  target.value = ''
}
// 删除待办
const deleteTodo = (id: number): void => {
  const index = todoList.value.findIndex((todo) => todo.id === id)
  todoList.value.splice(index, 1)
}
</script>
