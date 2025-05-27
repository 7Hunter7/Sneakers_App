<template>
  <div class="flex flex-col gap-4">
    <CartItem v-for="item in cartItems" :key="item.id" :item="item" />
  </div>
</template>

<script setup>
import CartItem from './CartItem.vue';
import { inject } from 'vue';

const { cartItems } = inject('cart');
</script>
