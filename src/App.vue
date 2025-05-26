<script setup>
import axios from 'axios';
import { onMounted, reactive, ref, watch } from 'vue';
import CardList from './components/CardList.vue';
import DrawerComponent from './components/DrawerComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';

const items = ref([]);

const filters = reactive({
  sortBy: '',
  searchQuery: ''
});

// Функция для обработки изменения сортировки
const onChangeSelect = (event) => {
  filters.sortBy = event.target.value;
};

// Загрузка данных при монтировании компонента
onMounted(async () => {
  try {
    const { data } = await axios.get('https://7c1179b9d2e1c831.mokky.dev/items');
    items.value = data;
  } catch (error) {
    console.error('Error fetching data:', error);
  }
})

// Слушаем изменения в sortBy и обновляем данные
watch(filters, async () => {
  try {
    const { data } = await axios.get('https://7c1179b9d2e1c831.mokky.dev/items?sortBy=' + filters.sortBy);
    items.value = data;
  } catch (error) {
    console.error('Error fetching data:', error);
  }
});
</script>

<template>
  <!-- <DrawerComponent /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <HeaderComponent />

    <div class="p-10">
      <div class="flex justify-between items-center mb-8">
        <h2 class="text-3xl font-bold">Все кроссовки</h2>
        <div class="flex items-center gap-4">
          <select @change="onChangeSelect"
            class="border border-gray-200 rounded-lg py-2 px-3 w-40 outline-none focus:border-lime-400" name="filter"
            id="">
            <option value="name">По названию</option>
            <option value="-price">По цене(сначала дешевые)</option>
            <option value="price">По цене(сначала дорогие)</option>
          </select>
          <div class="relative">
            <img class="absolute top-2.5 left-3" src="/search.svg" alt="Поиск">
            <input class="border border-gray-200 rounded-lg py-1.5 w-64 pl-10 pr-4 outline-none focus:border-lime-400"
              type="text" placeholder="Поиск..." />
          </div>
        </div>
      </div>
      <CardList :items="items" />
    </div>
  </div>
</template>

<style scoped></style>
