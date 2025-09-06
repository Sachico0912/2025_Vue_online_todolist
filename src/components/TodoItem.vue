<script setup>
const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
})

const emit = defineEmits(['delete-todo'])

function handelDeleteTodo(id) {
  emit('delete-todo', id)
}
</script>

<template>
  <li>
    <label class="todoList_label">
      <input class="todoList_input" type="checkbox" value="true" v-model="todo.status" />
      <span>{{ todo.content }}</span>
    </label>
    <a href="#" @click.prevent="handelDeleteTodo(todo.id)">
      <i class="fa fa-times"></i>
    </a>
  </li>
</template>
