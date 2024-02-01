<script setup lang="ts">
import AuraBackground from '../components/AuraBackground.vue'
</script>

<template>
  <section id="home">
    <div id="introduction">
      <h1>Lana Gordon</h1>
      <h2>Full<span>-</span>Stack Developer</h2>
    </div>
    <div id="background"><AuraBackground /></div>
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

#introduction {
  z-index: 2;
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  align-items: center;
  line-height: 1.3;
  text-align: center;
  color: var(--color-title);
}

h1 {
  font-size: 40px;
}

h2 {
  font-size: 20px;
}

span {
  font-family: TTFirsRegular;
}

#background {
  z-index: 1;
}

@media (min-width: 768px) {
  h1 {
    font-size: 65px;
  }
}
</style>
