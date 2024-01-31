<script setup lang="ts">
import Header from '../components/SectionHeader.vue'
import AboutBackground from '../components/AboutBackground.vue'
</script>

<template>
  <section id="about">
    <div class="container content">
      <div class="header">
        <Header title="About / Skills" />
      </div>
      <div class="left">
        <h4>About</h4>
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt
          ut labore et dolore magna aliqua. Aliquam nulla facilisi cras fermentum odio eu feugiat
          pretium.
        </p>
      </div>
      <div class="middle">
        <h4>Heading</h4>
        <ul>
          <li>One</li>
          <li>Two</li>
          <li>Three</li>
          <li>Four</li>
          <li>Five</li>
        </ul>
      </div>
      <div class="right">
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

    <div class="container background"><AboutBackground /></div>
  </section>
</template>

<style scoped>
#about {
  position: relative;
}

.container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.content {
  z-index: 2;
  width: 100%;
  height: auto;
  padding: 30px;
}

.background {
  z-index: 1;
}

div {
  margin-bottom: 26px;
}

h4 {
  margin-bottom: 10px;
}

p {
  font-weight: bold;
  font-family: BodyRegular;
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
  .content {
    width: 100%;
    height: var(--section-height);
    padding: 60px;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr min-content;
    grid-column-gap: 64px;
  }

  .header {
    grid-column: 1 / span 3;
    width: 33.3%;
  }

  div {
    margin-bottom: 0;
  }

  h4 {
    margin-bottom: 15px;
  }

  p {
    padding-right: 30px;
  }
}
</style>
