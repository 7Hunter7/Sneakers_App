<template>
  <h1>Hello</h1>
  <p>Welcome to the Sneakers App!</p>
  <button @click="handleClick">Click Me</button>
</template>


<script setup>
import { ref } from 'vue';

const message = ref('Hello, Sneakers App!');

function handleClick() {
  alert(message.value);
}

</script>