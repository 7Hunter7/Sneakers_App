<template>
  <header class="flex justify-between border-b border-slate-200 px-8 py-8">
    <RouterLink to="/">
      <div class="flex items-center gap-4">
        <img src="/logo.png" alt="Logo" class="w-12">
        <div>
          <h2 class="text-xl font-bold uppercase">Best Sneakers</h2>
          <p class="text-slate-400">Магазин лучших кроссовок</p>
        </div>
      </div>
    </RouterLink>

    <ul class="flex items-center gap-8">
      <li @click="() => emit('openDrawer')"
        class="flex items-center gap-2 text-gray-500 hover:text-gray-800 cursor-pointer">
        <img src="/cart.svg" alt="Cart">
        <b>{{ totalPrice }} руб.</b>
      </li>
      <RouterLink to="/favorites">
        <li class="flex items-center gap-2 text-gray-500 hover:text-black cursor-pointer">
          <img src="/heart.svg" alt="Favorites">
          <span>Закладки</span>
        </li>
      </RouterLink>
      <li class="flex items-center gap-2 text-gray-500 hover:text-black cursor-pointer">
        <img src="/profile.svg" alt="Profile">
        <span>Профиль</span>
      </li>
    </ul>
  </header>
</template>

<script setup>
defineProps({
  totalPrice: {
    type: Number,
    default: 0
  }
});


const emit = defineEmits(['openDrawer']);
</script>