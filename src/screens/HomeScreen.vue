<script setup lang="ts">
import AuraBackground from '../components/AuraBackground.vue'
</script>

<template>
  <section id="home">
    <div class="introduction">
      <h1>Lana Gordon</h1>
      <h2>Full<span>-</span>Stack Developer</h2>
    </div>
    <div class="background"><AuraBackground /></div>
  </section>
</template>

<style scoped>
#home {
  position: relative;
}

div {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.introduction {
  z-index: 2;
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  align-items: center;
  line-height: 1.3;
  color: var(--color-title);
}

span {
  font-family: TTFirsRegular;
}

.background {
  z-index: 1;
}

@media (min-width: 1024px) {
}
</style>
