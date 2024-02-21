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
  height: 100%;
}

#portfolio__background {
  z-index: 1;
}

#portfolio__content {
  width: 100%;
  height: 100%;
  position: relative;
  z-index: 2;
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: min-content 1fr;
}

#portfolio__content--projects {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto auto;
  margin-top: 36px;
}

.projects__row {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: auto;
}

.projects__row--card {
  min-height: 250px;
  display: flex;
  flex-direction: column;
  row-gap: 10px;
  margin-bottom: 25px;
}

.card__image {
  flex: 1;
  background-color: #f1f0ff;
  border-top-left-radius: 60px;
  border-top-right-radius: 60px;
}
.card__heading {
  font-weight: bold;
}

@media (min-width: 768px) {
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

@media (min-width: 1024px) {
  #portfolio {
    height: var(--section-height);
  }

  #portfolio__content {
    grid-template-columns: min-content 1fr;
    grid-template-rows: auto;
    column-gap: 80px;
  }

  #portfolio__content--projects {
    align-items: center;
    margin-top: 0px;
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
