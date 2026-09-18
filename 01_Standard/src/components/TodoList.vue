<script setup lang="ts">
import type {Todo} from "@/models/Todo.ts";
import TodoItem from "@/components/TodoItem.vue";


interface Props {
  todoList: Todo[]
}

const props = defineProps<Props>()

const emit = defineEmits<{
  (e: 'deleteTodo', id: number): void
  (e: 'toggleTodo', id: number): void
}>()


</script>

<template>
  <li>
    <TodoItem v-for="todo in todoList " :todo="todo" @delete="(id) => emit('deleteTodo', id)" @toggle="(id) => emit('toggleTodo', id)"></TodoItem>
  </li>
</template>

<style scoped></style>