<template>
  <div v-auto-animate class="flex flex-col gap-4">
    <CartItem v-for="item in cartItems" :key="item.id" :title="item.title" :imageUrl="item.imageUrl" :price="item.price"
      @on-click-remove="() => removeFromCart(item)" />
  </div>
</template>

<script setup>
import CartItem from './CartItem.vue';
import { inject } from 'vue';

const { cartItems, removeFromCart } = inject('cart');
</script>
