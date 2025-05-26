<template>
  <div class="grid grid-cols-4 gap-5">
    <CardComponent imageUrl="/sneakers/sneakers-1.jpg" title="Мужские Кроссовки Nike Blazer Mid Suede" :price="1205"
      isAdded isFavorite :onClickAdd="onClickAdd" :onClickFavorite="onClickFavorite" />
    <CardComponent imageUrl="/sneakers/sneakers-2.jpg" />
    <CardComponent imageUrl="/sneakers/sneakers-3.jpg" />
    <CardComponent imageUrl="/sneakers/sneakers-4.jpg" />
    <CardComponent imageUrl="/sneakers/sneakers-5.jpg" />
    <CardComponent imageUrl="/sneakers/sneakers-6.jpg" />
  </div>Мужские Кроссовки Nike Blazer Mid Suede
</template>

<script setup>
import CardComponent from './CardComponent.vue';

const onClickAdd = () => {
  console.log('Add to cart');
};

const onClickFavorite = () => {
  console.log('Add to favorites');
};
</script>