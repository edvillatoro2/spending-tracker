<template>
  <div class="flex flex-col gap-4">
    <h2 class="text-2xl uppercase">add new transaction</h2>
    <form action="" @submit.prevent="handleSubmit">
      <div class="flex flex-col gap-2 mb-4">
        <label for="text">title</label>
        <input
          type="text"
          id="text"
          v-model="text"
          class="w-full px-3 py-2 text-gray-700 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:border-blue-500 hover:border-gray-400"
          placeholder="enter title..."
        />
      </div>
      <div class="flex flex-col gap-2 mb-4">
        <label for="amount">amount</label>
        <input
          type="number"
          v-model="amount"
          id="amount"
          class="w-full px-3 py-2 text-gray-700 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:border-blue-500 hover:border-gray-400"
          placeholder="enter amount..."
        />
      </div>
      <button
        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded cursor-pointer"
        type="submit"
      >
        add transaction
      </button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useToast } from "vue-toastification";
import type { Transaction } from "../assets/types";

const toast = useToast();
const text = ref("");
const amount = ref(0);
const emit = defineEmits(["add-transaction"]);

const handleSubmit = () => {
  if (!text.value || !amount.value) {
    // display toast error if either field is empty
    toast.error("please fill in all fields");
    return;
  }
  const newTransaction: Transaction = {
    id: Date.now(),
    description: text.value,
    amount: amount.value,
  };
  emit("add-transaction", newTransaction);
  // reset form fields
  text.value = "";
  amount.value = 0;
};
</script>

<style scoped></style>
