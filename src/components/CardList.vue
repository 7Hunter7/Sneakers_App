<template>
  <div class="grid grid-cols-4 gap-5">
    <CardComponent v-for="item in items" :key="item.id" :imageUrl="item.imageUrl" :title="item.name" :price="item.price"
      :onClickAdd="onClickAdd" :onClickFavorite="onClickFavorite" />
  </div>
</template>

<script setup>
import CardComponent from './CardComponent.vue';

defineProps({
  items: Array
});

const onClickAdd = () => {
  console.log('Add to cart');
};

const onClickFavorite = () => {
  console.log('Add to favorites');
};
</script>