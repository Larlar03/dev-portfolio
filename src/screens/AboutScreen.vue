<script setup lang="ts">
import Header from '../components/SectionHeader.vue'
</script>

<template>
  <section id="about">
    <div class="header">
      <Header title="About & Skills" />
    </div>
    <div class="left">left</div>
    <div class="middle">middle</div>
    <div class="right">right</div>
  </section>
</template>

<style scoped>
#about {
  width: 100%;
  padding: 60px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 50% 50%;
  background-color: darkgrey;
}

.header {
  grid-column: 1 / span 3;
  width: 33.3%;
}

div {
  border: 1px solid orange;
}

@media (min-width: 1024px) {
}
</style>
