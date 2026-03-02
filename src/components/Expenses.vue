<template>
  <div class="flex bg-white shadow-sm border border-slate-200 rounded-lg p-2">
    <div
      class="flex-1 h-full flex flex-col justify-center items-center border-r border-slate-200"
    >
      <h3 class="text-lg font-bold">Income</h3>
      <p>${{ income }}</p>
    </div>
    <div class="flex-1 h-full flex flex-col justify-center items-center">
      <h3 class="text-lg font-bold">Expenses</h3>
      <p>${{ expenses }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  income: {
    type: Number,
    required: true,
  },
  expenses: {
    type: Number,
    required: true,
  },
});
</script>

<style scoped></style>
