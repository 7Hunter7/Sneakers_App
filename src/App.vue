<script setup>
import CartComponent from './components/CartComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';
</script>

<template>
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <HeaderComponent />
    <h2 class="text-3xl text-left font-bold my-5 px-8">Все кроссовки</h2>
    <CartComponent />
    <CartComponent />
    <CartComponent />
    <CartComponent />
    <CartComponent />
    <CartComponent />
  </div>
</template>

<style scoped></style>
