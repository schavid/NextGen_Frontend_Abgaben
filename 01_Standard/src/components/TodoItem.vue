<script setup lang="ts">

import type { Todo } from "../models/Todo.ts";


interface Props {
  todo: Todo
}


const props = defineProps<Props>()

const emit = defineEmits<{
  (e: 'delete', id: number): void
  (e: 'toggle', id: number): void
}>()

</script>

<template>

  <div class="todo-item">
    <input :id="'checkbox-' + todo.id" type="checkbox" :checked="todo.done" @change="emit('toggle', todo.id)">
    <label :for="'checkbox-' + todo.id">

    <span :class="{ 'erledigt': todo.done }">
      {{ todo.text }}
    </span>

    </label>
    <button @click="emit('delete', todo.id)">Löschen</button>
  </div>
</template>

<style scoped>
.todo-item {
  margin-bottom: 8px;
  display: flex;
  gap: 10px;
}
.erledigt {
  text-decoration: line-through;
  color: gray;
}
</style>