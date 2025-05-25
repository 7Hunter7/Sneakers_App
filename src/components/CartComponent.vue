<template>
  <div
    class="relative bg-white p-8 border border-slate-100 rounded-3xl cursor-pointer hover:-translate-y-2 hover:shadow-xl transition">
    <img src="/like-2.svg" alt="Like" class="absolute top-2 left-2">
    <img :src="imageUrl" alt="Sneakers">
    <h2 class="mt-2">{{ title }}</h2>
    <div class="flex justify-between mt-5">
      <div class="flex flex-col">
        <span class="text-slate-400 uppercase">Цена:</span>
        <b>{{ price }} руб.</b>
      </div>
      <img src="/plus.svg" alt="Plus">
    </div>
  </div>
</template>

<script setup>
defineProps({
  imageUrl: String,
  title: String,
  price: Number
});
</script>