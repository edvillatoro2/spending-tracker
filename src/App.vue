<script setup lang="ts">
import AddTransaction from "./components/AddTransaction.vue";
import Balance from "./components/Balance.vue";
</script>

<template>
  <header>
    <div class="wrapper">spending tracker</div>
  </header>

  <main>
    <div>
      <Balance :total="1000" />
      <AddTransaction :total="1000" />
    </div>
  </main>
</template>

<style scoped></style>
