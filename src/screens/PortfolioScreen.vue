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
      <div id="portfolio__content--projects">
        <div class="projects__row">
          <div class="projects__row--card">
            <div class="card__image"></div>
            <h4 class="card__heading">One</h4>
          </div>
          <div class="projects__row--card">
            <div class="card__image"></div>
            <h4 class="card__heading">Two</h4>
          </div>
          <div class="projects__row--card">
            <div class="card__image"></div>
            <h4 class="card__heading">Three</h4>
          </div>
        </div>
        <div class="projects__row">
          <div class="projects__row--card">
            <div class="card__image"></div>
            <h4 class="card__heading">Four</h4>
          </div>
          <div class="projects__row--card">
            <div class="card__image"></div>
            <h4 class="card__heading">Five</h4>
          </div>
          <div class="projects__row--card">
            <div class="card__image"></div>
            <h4 class="card__heading">Six</h4>
          </div>
        </div>
      </div>
    </div>
    <div id="portfolio__background" class=""><GradientBackground /></div>
  </section>
</template>

<style scoped>
#portfolio {
  position: relative;
  height: calc(var(--section-height) * 2);
}

#portfolio__background {
  z-index: 1;
}

#portfolio__content {
  width: 100%;
  height: 100%;
  position: absolute;
  z-index: 2;
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: min-content 1fr;
}

#portfolio__content--projects {
  display: flex;
  flex-wrap: wrap;
}

.projects__row {
  display: flex;
  flex-wrap: wrap;
  row-gap: 30px;
  width: 100%;
}

.projects__row--card {
  flex-basis: 100%; /* Initial size */
  flex-grow: 1; /* Allow item to grow */
  flex-shrink: 0; /* Prevent item from shrinking */
  height: 300px;
  display: flex;
  flex-direction: column;
}

.card__image {
  width: 100%;
  height: 85%;
  border-top-left-radius: 60px;
  border-top-right-radius: 60px;
  margin-bottom: 10px;
  background-color: #f1f0ff;
}

.card__heading {
  font-weight: bold;
}

@media (min-width: 768px) {
  #portfolio {
    height: var(--section-height);
  }

  #portfolio__content {
    grid-template-columns: min-content 1fr;
    grid-template-rows: 1fr;
    column-gap: 80px;
  }

  .projects__row {
    display: flex;
    flex-wrap: wrap;
    row-gap: 0;
    column-gap: 30px;
    width: 100%;
  }

  .projects__row--card {
    flex-basis: 30%; /* Shrink to 30% on larger screens */
    height: 250px;
  }
}
</style>
