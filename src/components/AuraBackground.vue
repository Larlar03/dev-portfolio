<script setup lang="ts">
import { onMounted, ref } from 'vue'

const cursorAura = ref<HTMLDivElement | null>(null)
const cursorX = ref(0)
const cursorY = ref(0)
const targetX = ref(0)
const targetY = ref(0)

const moveAura = (): void => {
  // How close aura is to cursor center
  cursorX.value += (targetX.value - cursorX.value) / 10
  cursorY.value += (targetY.value - cursorY.value) / 10

  if (cursorAura.value) {
    cursorAura.value.style.transform = `translate(${Math.round(cursorX.value)}px, ${Math.round(cursorY.value)}px)`
  }

  requestAnimationFrame((): void => {
    moveAura()
  })
}

onMounted(() => {
  if (cursorAura.value) {
    window.addEventListener('mousemove', (event: MouseEvent) => {
      targetX.value = event.clientX
      targetY.value = event.clientY
    })

    moveAura()
  }
})
</script>

<template>
  <div id="gradient-background">
    <div class="aura-container">
      <div class="aura aura-1"></div>
      <div class="aura aura-2"></div>
      <div class="aura aura-3"></div>
      <div class="aura aura-4"></div>
      <div class="cursor-aura" ref="cursorAura"></div>
    </div>
  </div>

  <!-- Filter Effects -->
  <svg xmlns="http://www.w3.org/2000/svg">
    <defs>
      <filter id="auraBgFilter">
        <!-- Blur filter -->
        <feGaussianBlur in="SourceGraphic" stdDeviation="125" result="blur" />
        <!-- Changes colors based on a transformation matrix -->
        <feColorMatrix
          in="blur"
          mode="matrix"
          values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -8"
          result="color"
        />
        <!-- Blend together using blend modes -->
        <feBlend in="blur" in2="color" />
      </filter>
    </defs>
  </svg>
</template>

<style scoped>
svg {
  display: none;
}

#gradient-background {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  /* background: linear-gradient(140deg, rgba(var(--gradient-4), 1), rgba(var(--gradient-3), 1)); */
  background-image: linear-gradient(
    100deg,
    var(--gradient-3) 0%,
    var(--gradient-4) 60%,
    var(--gradient-5) 80%,
    var(--gradient-6) 100%
  );
  overflow: hidden;
}

.aura-container {
  filter: url(#auraBgFilter);
  width: 100%;
  height: 100%;
}

.aura {
  position: absolute;
  width: var(--moving-circle-size);
  height: var(--moving-circle-size);
  background-repeat: no-repeat;
  mix-blend-mode: var(--blending);
  opacity: 1;
}

.aura-1 {
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-maximum-blue-purple), 1) 0,
    rgba(var(--rgb-maximum-blue-purple), 0) 50%
  );
  top: calc(50% - var(--moving-circle-size) / 2);
  left: calc(50% - var(--moving-circle-size) / 2);
  transform-origin: calc(50% + 220px) calc(50% + 100px);
  animation: moveInCircle 10s reverse infinite;
}

.aura-2 {
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-middle-blue-green), 1) 0,
    rgba(var(--rgb-middle-blue-green), 0) 50%
  );
  top: calc(50% - var(--moving-circle-size) / 2);
  left: calc(50% - var(--moving-circle-size) / 2);
  transform-origin: calc(50% - 300px);
  animation: moveInCircle 10s linear infinite;
}
.aura-3 {
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-pale-lavender), 1) 0,
    rgba(var(--rgb-pale-lavender), 0) 50%
  );
  top: calc(50% - var(--moving-circle-size) / 2 - 200px);
  left: calc(50% - var(--moving-circle-size) / 2 + 300px);
  transform-origin: calc(50% - 200px);
  animation: moveInCircle 10s linear infinite;
}
.aura-4 {
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-pale-cornflower-blue), 1) 0,
    rgba(var(--rgb-pale-cornflower-blue), 0) 50%
  );
  top: calc(50% - var(--moving-circle-size) / 2 - 200px);
  left: calc(50% - var(--moving-circle-size) / 2 - 400px);
  transform-origin: calc(50% + 220px) calc(50% + 100px);
  animation: moveInCircle 20s reverse infinite;
}

.cursor-aura {
  background: radial-gradient(
    circle at center,
    rgba(var(--cursor-color), 1) 0,
    rgba(var(--cursor-color), 0) 20%
  );
  position: absolute;
  width: 100%;
  height: 100%;
  top: -50%;
  left: -50%;
  opacity: 1;
}

@keyframes moveInCircle {
  0% {
    transform: rotate(0deg);
  }
  50% {
    transform: rotate(180deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
