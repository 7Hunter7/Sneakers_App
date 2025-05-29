<template>
  <div class="fixed top-0 left-0 w-full h-full bg-black/70 z-10">
    <div class="fixed top-0 right-0 w-96 h-full bg-white z-20 p-8">
      <DrawerHead />
      <div v-if="!totalPrice || orderId" class="flex items-center h-full">
        <InfoBlock v-if="!totalPrice && !orderId" title="Корзина пустая"
          description="Добавьте хотя бы одну пару кроссовок, чтобы сделать заказ" imageUrl="package-icon.png" />
        <InfoBlock v-if="orderId" title="Заказ оформлен!"
          :description="`Ваш заказ №${orderId} скоро будет передан курьерской доставке`"
          imageUrl="order-success-icon.png" />
      </div>
      <CartItemList />
      <div v-if="totalPrice" class="mt-8 flex flex-col gap-4">
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
        <button :disabled="buttonDisabled" @click="createOrder"
          class="bg-lime-500 w-full rounded-xl py-3 mt-4 text-white cursor-pointer transition hover:bg-lime-600 active:bg-lime-700 disabled:bg-slate-300">Оформить
          заказ</button>
      </div>
    </div>

  </div>
</template>

<script setup>
import axios from 'axios';
import { computed, inject, ref } from 'vue';
import DrawerHead from './DrawerHead.vue';
import InfoBlock from './InfoBlock.vue';
import CartItemList from './CartItemList.vue';

const props = defineProps({
  totalPrice: {
    type: Number,
    default: 0
  },
  vatPrice: {
    type: Number,
    default: 0
  }
});

const { closeDrawer, cartItems } = inject('cart');

const isCreating = ref(false);
const orderId = ref(null);
const cartIsEmpty = computed(() => cartItems.value.length === 0);
const buttonDisabled = computed(() => isCreating.value || cartIsEmpty.value);

// Функция для создания заказа
const createOrder = async () => {
  try {
    isCreating.value = true;
    const { data } = await axios.post(`https://7c1179b9d2e1c831.mokky.dev/orders`, {
      items: cartItems.value,
      totalPrice: props.totalPrice,
    });
    // Очистка корзины после успешного создания заказа
    cartItems.value = [];
    orderId.value = data.id;
    return data;
  } catch (error) {
    console.error('Error creating order:', error);
  } finally {
    isCreating.value = false;
  }
};
</script>