<template>
  <div class="fixed top-0 left-0 w-full h-full bg-black/70 z-10">
    <div class="fixed top-0 right-0 w-96 h-full bg-white z-20 p-8">
      <DrawerHead />
      <CartItemList />
      <div class="mt-8 flex flex-col gap-4">
        <div class="flex gap-2">
          <span>Итого:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ totalPrice }} руб.</b>
        </div>
        <div class="flex gap-2">
          <span>Налог 5%</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ vatPrice }} руб.</b>
        </div>
      </div>
      <button :disabled="totalPrice ? false : true" @click="emit('createOrder')"
        class="bg-lime-500 w-full rounded-xl py-3 mt-4 text-white cursor-pointer transition hover:bg-lime-600 active:bg-lime-700 disabled:bg-slate-300">Оформить
        заказ</button>
    </div>

  </div>
</template>

<script setup>
import DrawerHead from './DrawerHead.vue';
import CartItemList from './CartItemList.vue';

defineProps({
  totalPrice: {
    type: Number,
    default: 0
  },
  vatPrice: {
    type: Number,
    default: 0
  }
});

const emit = defineEmits(['createOrder']);
</script>