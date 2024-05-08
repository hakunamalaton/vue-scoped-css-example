<script setup>
import BaseChild from './BaseChild.vue'
</script>

<template>
  <BaseChild>
    <span class="text-blue">Base Child Slots</span>
  </BaseChild>
</template>

<style scoped>
.text-blue {
  color: blue;
}
</style>
