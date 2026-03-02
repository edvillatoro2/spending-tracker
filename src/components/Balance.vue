<template>
  <div class="balance">
    <h2 class="text-xl font-light uppercase">Your Balance</h2>
    <p class="text-lg font-bold">${{ total }}</p>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>

<style scoped>
.balance {
  color: #42b883;
}
</style>
