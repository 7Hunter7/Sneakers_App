<template>
  <div
    class="relative bg-white p-8 border border-slate-100 rounded-3xl cursor-pointer hover:-translate-y-2 hover:shadow-xl transition">
    <img v-if="onClickFavorite" :src="!isFavorite ? '/like-1.svg' : 'like-2.svg'" alt="Like"
      class="absolute top-2 left-2" @click="onClickFavorite">
    <img :src="imageUrl" alt="Sneakers">
    <h2 class="mt-2">{{ title }}</h2>
    <div class="flex justify-between mt-5">
      <div class="flex flex-col">
        <span class="text-slate-400 uppercase">Цена:</span>
        <b>{{ price }} руб.</b>
      </div>
      <img v-if="onClickAdd" :src="!isAdded ? '/plus.svg' : '/checked.svg'" alt="Plus" @click="onClickAdd"
        class="cursor-pointer hover:scale-110 transition">
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  id: Number,
  imageUrl: String,
  title: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function
});

</script>