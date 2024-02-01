<script setup lang="ts">
import Header from '../components/SectionHeader.vue'
import GradientBackground from '@/components/GradientBackground.vue'
// const props = defineProps({})
</script>

<template>
  <section id="portfolio">
    <div id="portfolio__content" class="container">
      <div id="portfolio__content--header">
        <Header title="Portfolio" subtitle="Personal Projects" />
      </div>
    </div>
    <div id="portfolio__background" class=""><GradientBackground /></div>
  </section>
</template>

<style scoped>
#portfolio {
  position: relative;
}

#portfolio__content {
  z-index: 2;
  width: 100%;
  height: auto;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

#portfolio__background {
  z-index: 1;
}

@media (min-width: 768px) {
}
</style>
