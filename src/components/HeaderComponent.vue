<template>
  <header class="flex justify-between border-b border-slate-300 px-8 py-8">
    <div class="flex items-center gap-4">
      <img src="/logo.png" alt="Logo" class="w-12">
      <div>
        <h2 class="text-xl font-bold uppercase">Best Sneakers</h2>
        <p class="text-slate-400">Магазин лучших кроссовок</p>
      </div>
    </div>

    <ul class="flex items-center gap-8">
      <li class="flex items-center gap-3 text-gray-500">
        <img src="/cart.svg" alt="Cart">
        <b>Стоимость</b>
      </li>
      <li class="flex items-center gap-3 text-gray-500">
        <img src="/heart.svg" alt="Favorites">
        <span>Закладки</span>
      </li>
      <li class="flex items-center gap-3 text-gray-500">
        <img src="/profile.svg" alt="Profile">
        <span>Профиль</span>
      </li>
    </ul>
  </header>
</template>


<script setup>
</script>