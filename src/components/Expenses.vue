<template>
  <div class="expenses">
    <h2>Expenses</h2>
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
    }
})
</script>

<style scoped>
.expenses {
  color: #ff5252;
}
</style>