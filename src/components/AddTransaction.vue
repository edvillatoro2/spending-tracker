<template>
  <div class="balance">
    <h2 class="text-2xl uppercase">add new transaction</h2>
    <form action="">
        <div>
            <label for="text">title</label>
            <input type="text" id="text" placeholder="enter title..." />
        </div>
        <div>
            <label for="amount">amount</label>
            <input type="number" id="amount" placeholder="enter amount..." />
        </div>
    </form>
  </div>
</template>

<script setup lang="ts">
</script>

<style scoped>
.balance {
  color: #42b883;
}
</style>