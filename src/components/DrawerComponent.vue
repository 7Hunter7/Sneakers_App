<template>
  <div class="fixed top-0 left-0 w-full h-full bg-black/70 z-10">
    <div class="fixed top-0 right-0 w-96 h-full bg-white z-20 p-8">
      <DrawerHead />
      <CartItemList />
    </div>
  </div>
</template>

<script setup>
import DrawerHead from './DrawerHead.vue';
import CartItemList from './CartItemList.vue';
</script>