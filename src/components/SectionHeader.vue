<script setup lang="ts">
defineProps<{
  title?: string
}>()
</script>

<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<style scoped>
@media (min-width: 1024px) {
}
</style>
