<template>
  <div class="container mx-auto">
    <div class="flex flex-col items-center justify-center min-h-screen">
      <main>
        <div class="flex items-center justify-center mb-8">
          <h1 class="text-4xl uppercase font-semibold text-amber-700">
            spending tracker
          </h1>
        </div>
        <div class="flex flex-col gap-4">
          <Balance :total="1000" />
          <Expenses :income="1000" :expenses="500" />
          <TransactionList
            :transactions="transactions"
            @delete-transaction="handleTransactionDelete"
          />
          test
          <AddTransaction @add-transaction="handleTransactionAdd" />
        </div>
      </main>
    </div>
  </div>
</template>

<script setup lang="ts">
import AddTransaction from "./components/AddTransaction.vue";
import Balance from "./components/Balance.vue";
import Expenses from "./components/Expenses.vue";
import TransactionList from "./components/TransactionList.vue";

import { ref, computed, onMounted } from "vue";
import { useToast } from "vue-toastification";
import type { Transaction } from "./assets/types";

const toast = useToast();
const transactions = ref<Transaction[]>([]);

const handleTransactionDelete = (id: number) => {
  transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id,
  );
  toast.success("Transaction deleted!");
};

const handleTransactionAdd = (transaction: Transaction) => {
  transactions.value.push({
    id: transaction.id,
    description: transaction.description,
    amount: transaction.amount,
  });
  saveTransactionToLocalStorage();
  toast.success("Transaction added!");
};

// save transactions to local storage
const saveTransactionToLocalStorage = () => {
  localStorage.setItem("transactions", JSON.stringify(transactions.value));
};
</script>

<style scoped></style>
