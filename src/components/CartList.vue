<template>
  <div class="grid grid-cols-4 gap-5">
    <CartComponent imageUrl="/sneakers/sneakers-1.jpg" title="Мужские Кроссовки Nike Blazer Mid Suede" :price="1205"
      isAdded isFavorite />
    <CartComponent imageUrl="/sneakers/sneakers-2.jpg" />
    <CartComponent imageUrl="/sneakers/sneakers-3.jpg" />
    <CartComponent imageUrl="/sneakers/sneakers-4.jpg" />
    <CartComponent imageUrl="/sneakers/sneakers-5.jpg" />
    <CartComponent imageUrl="/sneakers/sneakers-6.jpg" />
  </div>Мужские Кроссовки Nike Blazer Mid Suede
</template>

<script setup>
import CartComponent from './CartComponent.vue';
</script>