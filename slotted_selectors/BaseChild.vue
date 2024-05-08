<script setup></script>

<template>
  <div>
    <slot />
  </div>
</template>

<style scoped>
:slotted(.text-blue) {
  color: yellow;
}
</style>
