  <template>
    <h2 class="text-2xl font-bold mb-8">Мои закладки</h2>
    <CardList :items="favorites" is-favorites />
  </template>

<script setup>
import axios from 'axios';
import { onMounted, ref } from 'vue';
import CardList from '../components/CardList.vue';

const favorites = ref([]);

onMounted(async () => {
  try {
    const { data } = await axios.get('https://7c1179b9d2e1c831.mokky.dev/favorites?_relations=items');
    // Сохраняем полученные данные
    favorites.value = data.map((obj) => obj.item);
  } catch (error) {
    console.error('Error fetching favorites:', error);
  }
});
</script>