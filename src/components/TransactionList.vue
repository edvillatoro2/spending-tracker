<template>
  <div class="">
    <h3>History</h3>
    <ul>
      <li v-for="transaction in transactions" :key="transaction.id">
        {{ transaction.text }} - {{ transaction.amount }}
        <button @click="deleteTransaction(transaction.id)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
interface Transaction {
  id: number;
  text: string;
  amount: number;
}
const props = defineProps<{
  transactions: Transaction[];
}>();

const emit = defineEmits(["delete-transaction"]);
const deleteTransaction = (id: number) => {
  emit("delete-transaction", id);
};
</script>

<style scoped></style>
