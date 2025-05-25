<template>
  <header class="flex justify-between border-b border-slate-200 px-8 py-8">
    <div class="flex items-center gap-4">
      <img src="/logo.png" alt="Logo" class="w-12">
      <div>
        <h2 class="text-xl font-bold uppercase">Best Sneakers</h2>
        <p class="text-slate-400">Магазин лучших кроссовок</p>
      </div>
    </div>

    <ul class="flex items-center gap-8">
      <li class="flex items-center gap-2 text-gray-500 hover:text-gray-800 cursor-pointer">
        <img src="/cart.svg" alt="Cart">
        <b>Стоимость</b>
      </li>
      <li class="flex items-center gap-2 text-gray-500 hover:text-black cursor-pointer">
        <img src="/heart.svg" alt="Favorites">
        <span>Закладки</span>
      </li>
      <li class="flex items-center gap-2 text-gray-500 hover:text-black cursor-pointer">
        <img src="/profile.svg" alt="Profile">
        <span>Профиль</span>
      </li>
    </ul>
  </header>
</template>


<script setup>
</script>