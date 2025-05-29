<template>
  <div class="w-72 mx-auto flex flex-col items-center justify-center gap-4">
    <img class="w-32 h-32 object-cover" :src="imageUrl" alt="`Image of ${title}`" />
    <div>
      <h3 class="text-center text-2xl font-medium">{{ title }}</h3>
      <p class="text-center text-gray-400 mt-2">{{ description }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  imageUrl: {
    type: String,
    required: true
  },
  title: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  }
});
</script>