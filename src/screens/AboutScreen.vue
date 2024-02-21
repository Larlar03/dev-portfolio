<script setup lang="ts">
import Header from '../components/SectionHeader.vue'
import NoiseBackground from '../components/NoiseBackground.vue'
</script>

<template>
  <section id="about">
    <div id="about__content" class="container">
      <div id="about__content--header">
        <Header title="About / Skills" />
      </div>
      <div id="about__content--left" class="column">
        <h4>About</h4>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt
          ut labore et dolore magna aliqua. Aliquam nulla facilisi cras fermentum odio eu feugiat
          pretium.
        </p>
      </div>
      <div id="about__content--middle" class="column">
        <h4>Heading</h4>
        <ul>
          <li>One</li>
          <li>Two</li>
          <li>Three</li>
          <li>Four</li>
          <li>Five</li>
        </ul>
      </div>
      <div id="about__content--right" class="column">
        <h4>Heading</h4>
        <ul>
          <li>One</li>
          <li>Two</li>
          <li>Three</li>
          <li>Four</li>
          <li>Five</li>
        </ul>
      </div>
    </div>
    <div id="about__background" class="container"><NoiseBackground /></div>
  </section>
</template>

<style scoped>
#about {
  position: relative;
}

#about__content {
  z-index: 2;
  width: 100%;
  height: auto;
}

#about__background {
  z-index: 1;
}

.container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.column {
  margin-top: 36px;
}

h4 {
  margin-bottom: 10px;
}

p {
  font-weight: bold;
  text-transform: uppercase;
}

ul {
  list-style: none;
  padding-left: 0;
}

li {
  font-weight: bold;
}

@media (min-width: 768px) {
  #about__content {
    width: 100%;
    height: var(--section-height);
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr min-content;
    grid-column-gap: 100px;
  }

  #about__content--header {
    grid-column: 1 / span 4;
    width: 33.3%;
  }

  #about__content--left {
    grid-column: 1 / span 2;
  }

  .column {
    margin-top: 0;
  }

  h4 {
    margin-bottom: 15px;
  }

  p {
    padding-right: 60px;
  }
}
</style>
