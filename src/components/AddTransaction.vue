<template>
  <div>
    <h3 class="text-lg font-bold mb-2">Add new transaction</h3>

    <form @submit.prevent="submitTransaction" class="space-y-3">
      <div>
        <label class="block text-sm font-medium mb-1">Text</label>
        <input
          v-model="text"
          type="text"
          class="w-full px-3 py-2 border rounded"
          placeholder="Enter description..."
        />
      </div>

      <div>
        <label class="block text-sm font-medium mb-1">
          Amount (negative = expense)
        </label>
        <input
          v-model="amount"
          @input="handleAmountInput"
          type="text"
          class="w-full px-3 py-2 border rounded"
          placeholder="0"
        />
      </div>

      <button
        class="w-full bg-green-500 text-white py-2 rounded hover:bg-green-600"
        :disabled="isDisabled"
        :class="{
          'opacity-50 cursor-not-allowed': isDisabled,
        }"
      >
        Add transaction
      </button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import { useToast } from "vue-toastification";

const emit = defineEmits(["add-transaction"]);
const toast = useToast();
const text = ref("");
const amount = ref("");

const isDisabled = computed(() => !text.value || !amount.value);

const formatCurrency = (value: string) => {
  const cleaned = value.replace(/[^0-9.-]/g, "");
  // allow user to type just "-"
  if (cleaned === "-") return "-";
  const number = Number(cleaned);

  if (isNaN(number)) return "";
  return number.toLocaleString("en-US");
};

const handleAmountInput = () => {
  amount.value = formatCurrency(amount.value);
};

const submitTransaction = () => {
  if (!text.value || !amount.value) {
    // Display a toast error message if either field is empty
    toast.error("Both fields must be filled.");
    return;
  }

  const cleanedAmount = Number(amount.value.replace(/,/g, ""));
  emit("add-transaction", {
    id: Date.now(),
    description: text.value,
    amount: cleanedAmount,
  });

  text.value = "";
  amount.value = "";
};
</script>
