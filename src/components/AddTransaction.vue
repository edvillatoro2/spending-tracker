<template>
  <div class="balance flex flex-col gap-4">
    <h2 class="text-2xl uppercase">add new transaction</h2>
    <form action="">
      <div class="flex flex-col gap-2 mb-4">
        <label for="text">title</label>
        <input type="text" id="text" placeholder="enter title..." />
      </div>
      <div class="flex flex-col gap-2 mb-4">
        <label for="amount">amount</label>
        <input type="number" id="amount" placeholder="enter amount..." />
      </div>
    </form>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.balance {
  color: #42b883;
}
</style>
