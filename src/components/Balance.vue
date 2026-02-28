<template>
  <div class="balance">
    <h2>Balance</h2>
    <h1 class="balance">{{ total }}</h1>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  total: {
    type: Number,
    required: true
  }
})
</script>

<style scoped>
.balance {
  color: #42b883;
}
</style>