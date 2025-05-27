<template>
  <div class="flex items-center gap-4 bg-white p-4 border border-slate-200 rounded-xl">
    <img class="w-16 h-16" :src="imageUrl" :alt="`Image of ${title}`" />
    <div class="flex flex-col">
      <p>{{ title }}</p>
      <div class="flex justify-between mt-2">
        <b>1{{ price }} руб.</b>
        <svg class="cursor-pointer transition opacity-40  hover:opacity-100" width="32" height="32" viewBox="0 0 32 32"
          fill="none" xmlns="http://www.w3.org/2000/svg">
          <path
            d="M20.0799 18.6155L17.6311 16.1667L20.0798 13.718C21.0241 12.7738 19.5596 11.3093 18.6154 12.2536L16.1667 14.7023L13.7179 12.2535C12.7738 11.3095 11.3095 12.7738 12.2535 13.7179L14.7023 16.1667L12.2536 18.6154C11.3093 19.5596 12.7738 21.0241 13.718 20.0798L16.1667 17.6311L18.6155 20.0799C19.5597 21.0241 21.0241 19.5597 20.0799 18.6155Z"
            fill="#B5B5B5" />
        </svg>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  id: Number,
  imageUrl: String,
  title: String,
  price: Number,
  count: Number,
  isAdded: Boolean,
  isFavorite: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function,
});
</script>