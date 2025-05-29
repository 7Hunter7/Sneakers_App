<template>
  <div class="flex justify-between items-center mb-8">
    <h2 class="text-3xl font-bold">Все кроссовки</h2>
    <div class="flex items-center gap-4">
      <select @change="onChangeSelect"
        class="border border-gray-200 rounded-lg py-2 px-3 w-40 outline-none focus:border-lime-400" name="filter" id="">
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
  <CardList :items="items" @add-to-favorite="addToFavorite" @add-to-cart="onClickAddPlus" />
</template>

<script setup>
import axios from 'axios';
import debounce from 'lodash.debounce';
import { onMounted, ref, reactive, inject, watch } from "vue";
import CardList from '../components/CardList.vue';

const { cartItems, addToCart, removeFromCart } = inject("cart");

const items = ref([]);

const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
});


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
      const favorite = favorites.find((fav) => fav.item_id === item.id);
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

// Функция для обработки изменения сортировки
const onChangeSelect = (event) => {
  filters.sortBy = event.target.value;
};

// Функция для обработки изменения поиска
const onChangeSearchInput = debounce((event) => {
  filters.searchQuery = event.target.value;
}, 400);

// Функция для добавления и удаления товара из корзины
const onClickAddPlus = async (item) => {
  if (!item.isAdded) {
    addToCart(item);
  } else {
    removeFromCart(item);
  }
};

// Функция для добавления и удаления товара из избранного
const addToFavorite = async (item) => {
  try {
    if (!item.isFavorite) {
      const obj = {
        item_id: item.id,
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

// Загрузка данных при монтировании компонента
onMounted(async () => {
  // Проверка наличия корзины в localStorage
  const savedCart = localStorage.getItem('cart');
  if (savedCart) {
    cartItems.value = JSON.parse(savedCart);
  }
  // Загрузка товаров и избранных товаров
  await fetchItems();
  await fetchFavoriteItems();
  // Установка флага isAdded для каждого товара в зависимости от наличия в корзине
  items.value = items.value.map((item) => ({
    ...item,
    isAdded: cartItems.value.some(cartItem => cartItem.id === item.id),
  }));
});

// Реактивное отслеживание изменений в фильтрах
watch(filters, fetchItems);

// Реактивное отслеживание изменений корзины
watch(cartItems, () => {
  items.value = items.value.map((item) => ({
    ...item,
    isAdded: false,
  }));
})
</script>