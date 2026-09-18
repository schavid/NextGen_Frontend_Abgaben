<script setup lang="ts">
import type {Todo} from "@/models/Todo.ts";
import TodoList from "@/components/TodoList.vue";
import {ref} from "vue";

const todoList = ref<Todo[]>([]);


function generateTodo(id: number, text: string, checked: boolean): Todo {
  return {
    id:  id,
    text: text,
    done: checked
  }
}

let todo1: Todo = generateTodo(1, "Feed the Cat", true);
let todo2: Todo = generateTodo(2, "Feed the dog", false);
let todo3: Todo = generateTodo(3, "Feed the horse", false);

todoList.value.push(todo1, todo2, todo3);

function deleteTodo(id: number) {
  todoList.value = todoList.value.filter(todo => todo.id !== id);
}

function toggleTodo(id: number) {
  const todo = todoList.value.find(t => t.id === id);
  if (todo) {
    todo.done = !todo.done;
  }
}

</script>

<template>
  <TodoList :todoList="todoList" @delete-todo="deleteTodo" @toggle-todo="toggleTodo"></TodoList>
</template>

<style scoped></style>