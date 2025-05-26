<script setup>
import CardList from './components/CardList.vue';
import DrawerComponent from './components/DrawerComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';

const items = [
  {
    "id": 1,
    "name": "Мужские Кроссовки Nike Blazer Mid Suede",
    "price": "1205",
    "imageUrl": "/sneakers/sneakers-1.jpg"
  },
  {
    "id": 2,
    "name": "Мужские Кроссовки Nike Air Max 270",
    "price": "1390",
    "imageUrl": "/sneakers/sneakers-2.jpg"
  },
  {
    "id": 3,
    "name": "Мужские Кроссовки Adidas Yeezy Boost 350",
    "price": "1790",
    "imageUrl": "/sneakers/sneakers-3.jpg"
  },
  {
    "id": 4,
    "name": "Мужские Кроссовки Puma RS-X",
    "price": "1120",
    "imageUrl": "/sneakers/sneakers-4.jpg"
  },
  {
    "id": 5,
    "name": "Мужские Кроссовки Reebok Classic",
    "price": "980",
    "imageUrl": "/sneakers/sneakers-5.jpg"
  },
  {
    "id": 6,
    "name": "Мужские Кроссовки New Balance 574",
    "price": "1245",
    "imageUrl": "/sneakers/sneakers-6.jpg"
  }
]
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
      <CardList :items="items" />
    </div>
  </div>
</template>

<style scoped></style>
