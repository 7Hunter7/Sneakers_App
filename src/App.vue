<script setup>
import axios from 'axios';
import { onMounted, provide, reactive, ref, watch } from 'vue';
import CardList from './components/CardList.vue';
import DrawerComponent from './components/DrawerComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';

const items = ref([]);
const cartItems = ref([]);


const drawerOpen = ref(false);

// Функция открытия Карзины (Drawer)
const openDrawer = () => {
  drawerOpen.value = true;
};

// Функция закрытия Карзины (Drawer)
const closeDrawer = () => {
  drawerOpen.value = false;
};

const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
});

// Функция для обработки изменения сортировки
const onChangeSelect = (event) => {
  filters.sortBy = event.target.value;
};

// Функция для обработки изменения поиска
const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value;
};

// Функция для получения данных с сервера
const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy,
    };

    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`;
    }

    const { data } = await axios.get(
      `https://7c1179b9d2e1c831.mokky.dev/items`,
      { params }
    );
    items.value = data.map((item) => ({
      ...item,
      isAdded: false,
      isFavorite: false,
      favoriteId: null
    }));
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

// Функция для получения избранных товаров с сервера
const fetchFavoriteItems = async () => {
  try {
    const { data: favorites } = await axios.get(
      `https://7c1179b9d2e1c831.mokky.dev/favorites`,
    );
    items.value = items.value.map((item) => {
      const favorite = favorites.find((fav) => fav.productId === item.id);
      if (!favorite) {
        return item;
      }
      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id,
      };
    });
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

// Функция для добавления и удаления товара из избранного
const addToFavorite = async (item) => {
  try {
    if (!item.isFavorite) {
      const obj = {
        productId: item.id,
      };
      item.isFavorite = true;
      const { data } = await axios.post(
        `https://7c1179b9d2e1c831.mokky.dev/favorites`,
        obj
      );
      item.favoriteId = data.id;
    } else {
      item.isFavorite = false;
      await axios.delete(
        `https://7c1179b9d2e1c831.mokky.dev/favorites/${item.favoriteId}`
      );
      item.favoriteId = null;
    }
  } catch (error) {
    console.error('Error adding to favorites:', error);
  }
};

// Функция для добавления и удаления товара из корзины
const addToCart = async (item) => {
  if (!item.isAdded) {
    cartItems.value.push(item);
    item.isAdded = true;
  } else {
    cartItems.value.splice(
      cartItems.value.indexOf(item),
      1
    );
    item.isAdded = false;
  }
};
// Загрузка данных при монтировании компонента
onMounted(async () => {
  await fetchItems();
  await fetchFavoriteItems();
});
// Реактивное отслеживание изменений в фильтрах
watch(filters, fetchItems);

provide('cart', {
  cartItems,
  openDrawer,
  closeDrawer
});
</script>

<template>
  <DrawerComponent v-if="drawerOpen" />
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <HeaderComponent @open-drawer="openDrawer" />

    <div class="p-10">
      <div class="flex justify-between items-center mb-8">
        <h2 class="text-3xl font-bold">Все кроссовки</h2>
        <div class="flex items-center gap-4">
          <select @change="onChangeSelect"
            class="border border-gray-200 rounded-lg py-2 px-3 w-40 outline-none focus:border-lime-400" name="filter"
            id="">
            <option value="name">По названию</option>
            <option value="price">По цене(сначала дешевые)</option>
            <option value="-price">По цене(сначала дорогие)</option>
          </select>
          <div class="relative">
            <img class="absolute top-2.5 left-3" src="/search.svg" alt="Поиск">
            <input @input="onChangeSearchInput"
              class="border border-gray-200 rounded-lg py-1.5 w-64 pl-10 pr-4 outline-none focus:border-lime-400"
              type="text" placeholder="Поиск..." />
          </div>
        </div>
      </div>
      <CardList :items="items" @add-to-favorite="addToFavorite" @add-to-cart="addToCart" />
    </div>
  </div>
</template>

<style scoped></style>
