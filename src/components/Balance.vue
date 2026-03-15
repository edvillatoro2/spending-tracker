<template>
  <div class="balance">
    <h2 class="text-xl font-light uppercase">Your Balance</h2>
    <p class="text-lg font-bold">{{ formattedTotal }}</p>
  </div>
</template>

<script setup lang="ts">
import { computed } from "vue";

const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});

const formattedTotal = computed(() => {
  return props.total.toLocaleString("en-US", {
    style: "currency",
    currency: "USD",
  });
});
</script>

<style scoped>
.balance {
  color: #42b883;
}
</style>
