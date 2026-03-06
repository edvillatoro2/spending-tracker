<template>
  <div class="flex flex-col gap-4">
    <h3 class="text-xl font-semibold">History</h3>
    <div v-for="transaction in transactions" :key="transaction.id">
      <div class="flex justify-between">
        {{ transaction.description }}
      </div>
      <div>
        {{ transaction.amount }}
      </div>
    </div>
    <button
      class="bg-red-500 hover:bg-red-700 text-white font-bold py-1 px-2 rounded cursor-pointer"
      @click="deleteTransaction(transaction.id)"
    >
      Delete
    </button>
  </div>
</template>

<script setup lang="ts">
import type { Transaction } from "../assets/types";
const props = defineProps({
  transactions: {
    type: Array as () => Transaction[],
    required: true,
  },
});

const emit = defineEmits(["delete-transaction"]);
const deleteTransaction = (id: number) => {
  emit("delete-transaction", id);
};
</script>

<style scoped></style>
