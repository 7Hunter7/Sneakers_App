<template>
  <div class="grid grid-cols-4 gap-5">
    <CardComponent v-for="item in items" :key="item.id" :id="item.id" :imageUrl="item.imageUrl" :title="item.title"
      :price="item.price" :isFavorite="item.isFavorite" :isAdded="item.isAdded"
      :onClickAdd="() => emit('addToCart', item)" :onClickFavorite="() => emit('addToFavorite', item)" />
  </div>
</template>

<script setup>
import CardComponent from './CardComponent.vue';

defineProps({
  items: Array
});

const emit = defineEmits(['addToFavorite', 'addToCart']);
</script>