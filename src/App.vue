<script setup lang="ts">
import Home from './screens/HomeScreen.vue'
import About from './screens/AboutScreen.vue'
import Portfolio from './screens/PortfolioScreen.vue'
import Contact from './screens/ContactScreen.vue'
</script>

<template>
  <main>
    <Home />
    <About />
    <Portfolio />
    <Contact />
  </main>
</template>

<style scoped>
main {
  width: 100%;
  height: 100%;
}

@media (min-width: 768px) {
}
</style>
