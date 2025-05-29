<template>
  <div v-auto-animate class="grid grid-cols-4 gap-5">
    <CardComponent v-for="item in items" :key="item.id" :id="item.id" :imageUrl="item.imageUrl" :title="item.title"
      :price="item.price" :isFavorite="item.isFavorite" :isAdded="item.isAdded"
      :onClickAdd="isFavorites ? nunll : () => emit('addToCart', item)"
      :onClickFavorite="isFavorites ? nunll : () => emit('addToFavorite', item)" />
  </div>
</template>

<script setup>
import CardComponent from './CardComponent.vue';

defineProps({
  items: Array,
  isFavorites: Boolean
});

const emit = defineEmits(['addToFavorite', 'addToCart']);
</script>