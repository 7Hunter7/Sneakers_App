<script setup>
import CardList from './components/CardList.vue';
import DrawerComponent from './components/DrawerComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';
</script>

<template>
  <!-- <DrawerComponent /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <HeaderComponent />

    <div class="p-10">
      <div class="flex justify-between items-center mb-8">
        <h2 class="text-3xl font-bold">Все кроссовки</h2>
        <div class="flex items-center gap-4">
          <select class="border border-gray-200 rounded-lg py-2 px-3 w-40 outline-none focus:border-lime-400"
            name="filter" id="">
            <option value="all">Все</option>
            <option value="new">Новинки</option>
            <option value="popular">Популярные</option>
            <option value="sale">Распродажа</option>
            <option value="cheap">Дешевые</option>
            <option value="expensive">Дорогие</option>
          </select>
          <div class="relative">
            <img class="absolute top-2.5 left-3" src="/search.svg" alt="Поиск">
            <input class="border border-gray-200 rounded-lg py-1.5 w-64 pl-10 pr-4 outline-none focus:border-lime-400"
              type="text" placeholder="Поиск..." />
          </div>
        </div>
      </div>
      <CardList />
    </div>
  </div>
</template>

<style scoped></style>
