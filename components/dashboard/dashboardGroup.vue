<template>
  <div class="group_title">
    <h1>{{$props.title}}</h1>
    <slot />
  </div>
</template>

<script setup>
// define props title and slot
const title = defineProps({
  title: {
    type: String,
    default: 'Title'
  }
})


</script>

<style scoped>

</style>