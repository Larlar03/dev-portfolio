<script setup lang="ts">
const props = defineProps({
  title: {
    type: String,
    default: 'Lorem Ipsum'
  },
  subtitle: String
})
</script>

<template>
  <header>
    <h4>{{ props.subtitle }}</h4>
    <h3>{{ props.title }}</h3>
  </header>
</template>

<style scoped>
@media (min-width: 768px) {
}
</style>
