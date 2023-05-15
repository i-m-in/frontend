<template>
  <div class="container">
    <img :src="url" alt="" class="avatar">
    <p class="name">{{name}}</p>
  </div>
</template>

<script setup lang="ts">

defineProps<{url: string, name: string}>()

</script>

<style scoped>
  .container {
    display: flex;
    gap: 1rem;
  }

  .name {
    font-weight: 600;
    font-size: 1.4rem;
  }

  .avatar {
    height: 2.4rem;
    border-radius: 50%;
  }
</style>