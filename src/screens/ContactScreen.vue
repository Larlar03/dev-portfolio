<script setup lang="ts">
import Header from '../components/SectionHeader.vue'
import NoiseBackgroundContact from '@/components/NoiseBackgroundContact.vue'

// const props = defineProps({})
const contactDetails = {
  email: 'email@gmail.com',
  github: 'www.github.com',
  linkedin: 'www.linkedin.com'
}
</script>

<template>
  <section id="contact">
    <div id="contact__content" class="container">
      <div id="contact__content--header">
        <Header title="Contact" />
      </div>
      <div class="contact__content--details">
        <h5>Lana Gordon</h5>
        <ul>
          <li>
            <a href="">{{ contactDetails.email }}</a>
          </li>
          <li>
            <a href="">{{ contactDetails.github }}</a>
          </li>
          <li>
            <a href="">{{ contactDetails.linkedin }}</a>
          </li>
        </ul>
      </div>
    </div>
    <div id="contact__background" class="container">
      <NoiseBackgroundContact></NoiseBackgroundContact>
    </div>
  </section>
</template>

<style scoped>
#contact {
  position: relative;
  height: calc(var(--section-height) / 2);
}

#contact__background {
  z-index: 1;
}

#contact__content {
  width: 100%;
  height: 100%;
  position: relative;
  z-index: 2;
  display: flex;
  flex-flow: column nowrap;
  justify-content: space-between;
}

.contact__content--details ul {
  padding: 0;
  list-style: none;
  font-family: TTFirsRegular;
}

@media (min-width: 768px) {
}
</style>
