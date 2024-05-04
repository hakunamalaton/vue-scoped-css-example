<script setup>
import BaseChild from './BaseChild.vue';
</script>

<template>
  <div>
    <BaseChild />
  </div>
</template>

<style scoped>
.base-child-wrapper-1 :deep(.text-green) {
  color: green;
}
</style>
