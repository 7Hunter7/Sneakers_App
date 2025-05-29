<script setup>
import axios from 'axios';
import { computed, provide, ref, watch } from 'vue';
import DrawerComponent from './components/DrawerComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';

const cartItems = ref([]);
const drawerOpen = ref(false);
const isCreatingOrder = ref(false);

const totalPrice = computed(
  () => cartItems.value.reduce((acc, item) => acc + item.price, 0)
);
const vatPrice = computed(
  () => Math.round(totalPrice.value * 0.05) // 5% НДС
);

// Функция открытия Карзины (Drawer)
const openDrawer = () => {
  drawerOpen.value = true;
};

// Функция закрытия Карзины (Drawer)
const closeDrawer = () => {
  drawerOpen.value = false;
};

const addToCart = async (item) => {
  cartItems.value.push(item);
  item.isAdded = true;
};

const removeFromCart = async (item) => {
  cartItems.value.splice(cartItems.value.indexOf(item), 1);
  item.isAdded = false;
};

// Функция для создания заказа
const createOrder = async () => {
  try {
    isCreatingOrder.value = true;
    const { data } = await axios.post(`https://7c1179b9d2e1c831.mokky.dev/orders`, {
      items: cartItems.value,
      totalPrice: totalPrice.value,
    });
    // Очистка корзины после успешного создания заказа
    cartItems.value = [];

    return data;
  } catch (error) {
    console.error('Error creating order:', error);
  } finally {
    isCreatingOrder.value = false;
  }
};

// Сохранение корзины в localStorage при изменении
watch(cartItems, () => {
  localStorage.setItem('cart', JSON.stringify(cartItems.value));
}, {
  deep: true
});


provide('cart', {
  cartItems,
  openDrawer,
  closeDrawer,
  addToCart,
  removeFromCart
});
</script>

<template>
  <DrawerComponent v-if="drawerOpen" :total-price="totalPrice" :vat-price="vatPrice" @create-order="createOrder"
    :is-creating-order="isCreatingOrder" />
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <HeaderComponent @open-drawer="openDrawer" :total-price="totalPrice" />

    <main class="p-10">
      <RouterView />
    </main>
  </div>
</template>

<style scoped></style>
