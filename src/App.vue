<script setup>
import CartList from './components/CartList.vue';
import DrawerComponent from './components/DrawerComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';
</script>

<template>
  <DrawerComponent />
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <HeaderComponent />

    <div class="p-10">
      <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
      <CartList />
    </div>
  </div>
</template>

<style scoped></style>
