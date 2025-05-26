<script setup>
import CartList from './components/CartList.vue';
import DrawerComponent from './components/DrawerComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';
</script>

<template>
  <!-- <DrawerComponent /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <HeaderComponent />

    <div class="p-10">
      <div class="flex justify-between">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
        <div class="relative">
          <img class="absolute top-2.5 left-3" src="/search.svg" alt="Поиск">
          <input class="border border-gray-200 rounded-lg py-1.5 w-64 pl-10 pr-4 outline-none focus:border-lime-400"
            type="text" placeholder="Поиск..." />
        </div>
      </div>
      <CartList />
    </div>
  </div>
</template>

<style scoped></style>
