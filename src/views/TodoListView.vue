<script setup lang="ts">
import TodoForm from '@/components/TodoForm.vue'
import TodoList from '@/components/TodoList.vue'
import { ref } from 'vue'

const todos = ref([
  { id: 1, content: '把冰箱發霉的檸檬拿去丟', status: true },
  { id: 2, content: '打電話叫男朋友匯款給我', status: false },
])

function addTodo(content) {
  if (content.value.trim() !== '') {
    todos.value.push({
      id: Date.now(),
      content: content.value,
      status: false,
    })
    content.value = ''
  }
}

function deleteTodo(id) {
  todos.value = todos.value.filter((e) => e.id !== id)
}
</script>

<template>
  <div id="todoListPage" class="bg-half">
    <nav>
      <h1><a href="#">ONLINE TODO LIST</a></h1>
      <ul>
        <li class="todo_sm">
          <a href="#"><span>王小明的代辦</span></a>
        </li>
        <li><a href="#loginPage">登出</a></li>
      </ul>
    </nav>
    <div class="conatiner todoListPage vhContainer">
      <div class="todoList_Content">
        <TodoForm />
        <TodoList v-if="todos.length" :todos="todos" @delete-todo="deleteTodo" />
        <p v-else>目前無待辦事項</p>
      </div>
    </div>
  </div>
</template>
