<template>
  <div class="px-2 w-1/2 mb-2">
    <div class="p-4 bg-white rounded text-center">
      <p class="text-sm text-gray-500 mb-2">{{ cardName }}</p>
      <h3 class="text-lg text-bold">{{ cardValue }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cardName: String,
    cardValue: [String, Number],
  },
};
</script>