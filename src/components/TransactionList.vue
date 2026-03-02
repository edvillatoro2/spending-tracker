<template>
  <div class="">
    <h3 class="text-xl font-semibold">History</h3>
    <ul>
      <li v-for="transaction in transactions" :key="transaction.id">
        {{ transaction.description }} - {{ transaction.amount }}
        <button
          class="bg-red-500 hover:bg-red-700 text-white font-bold py-1 px-2 rounded cursor-pointer ml-2"
          @click="deleteTransaction(transaction.id)"
        >
          Delete
        </button>
      </li>
    </ul>
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
