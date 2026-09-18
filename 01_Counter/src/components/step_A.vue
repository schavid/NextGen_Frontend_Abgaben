<script setup lang="ts">

import { ref } from 'vue'

const counter = ref(0)

function add() {
  counter.value++
}

function substract() {
  counter.value--
}

</script>

<template>

  <h1>Counter: {{counter}}</h1>

  <button id="add" @click="add">
    + add
  </button>

  <button id="substract" @click="substract">
    - substract
  </button>


</template>
