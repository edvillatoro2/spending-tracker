<template>
  <div>
    <h3 class="text-lg font-bold mb-2">History</h3>

    <ul class="space-y-2">
      <li
        v-for="transaction in transactions"
        :key="transaction.id"
        class="flex justify-between items-center bg-white border rounded p-2 shadow-sm"
        :class="transaction.amount < 0 ? 'border-red-400' : 'border-green-400'"
      >
        <span>{{ transaction.description }}</span>

        <div class="flex items-center gap-3">
          <span
            :class="transaction.amount < 0 ? 'text-red-600' : 'text-green-600'"
          >
            {{ currency.format(transaction.amount) }}
          </span>

          <button
            @click="$emit('delete-transaction', transaction.id)"
            class="text-red-500 hover:text-red-700"
          >
            x
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  transactions: {
    id: number;
    description: string;
    amount: number;
  }[];
}>();

const currency = new Intl.NumberFormat("en-US", {
  style: "currency",
  currency: "USD",
});
</script>
