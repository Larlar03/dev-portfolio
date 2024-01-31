<script setup lang="ts">
import { onMounted, ref } from 'vue'

defineProps<{
  colors?: number[][]
}>()

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
  <!-- Filter Effects -->
  <svg xmlns="http://www.w3.org/2000/svg">
    <defs>
      <filter id="filterEffects">
        <!-- Blur filter -->
        <feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" />
        <!-- Changes colors based on a transformation matrix -->
        <feColorMatrix
          in="blur"
          mode="matrix"
          values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -8"
          result="filterEffects"
        />
        <!-- Blend together using blend modes -->
        <feBlend in="SourceGraphic" in2="filterEffects" />
      </filter>
    </defs>
  </svg>

  <!-- Content -->
  <div id="gradient-background">
    <div class="aura-container">
      <div class="aura aura-1"></div>
      <div class="aura aura-2"></div>
      <div class="aura aura-3"></div>
      <div class="aura aura-4"></div>
      <div class="cursor-aura" ref="cursorAura"></div>
    </div>
  </div>
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
  background: linear-gradient(140deg, var(--bg-color-1), var(--bg-color-2));
  overflow: hidden;
}

.aura-container {
  filter: url(#filterEffects) blur(10px);
  width: 100%;
  height: 100%;
}

.aura {
  position: absolute;
  width: var(--circle-size);
  height: var(--circle-size);
  background-repeat: no-repeat;
  mix-blend-mode: var(--blending);
  opacity: 1;
}

.aura-1 {
  background: radial-gradient(
    circle at center,
    rgba(var(--color-1), 1) 0,
    rgba(var(--color-1), 0) 50%
  );
  top: calc(50% - var(--circle-size) / 2);
  left: calc(50% - var(--circle-size) / 2);
  transform-origin: calc(50% + 220px) calc(50% + 100px);
  animation: moveInCircle 10s reverse infinite;
}

.aura-2 {
  background: radial-gradient(
    circle at center,
    rgba(var(--color-2), 1) 0,
    rgba(var(--color-2), 0) 50%
  );
  top: calc(50% - var(--circle-size) / 2);
  left: calc(50% - var(--circle-size) / 2);
  transform-origin: calc(50% - 300px);
  animation: moveInCircle 10s linear infinite;
}
.aura-3 {
  background: radial-gradient(
    circle at center,
    rgba(var(--color-3), 1) 0,
    rgba(var(--color-3), 0) 50%
  );
  top: calc(50% - var(--circle-size) / 2 - 200px);
  left: calc(50% - var(--circle-size) / 2 + 300px);
  transform-origin: calc(50% - 200px);
  animation: moveInCircle 10s linear infinite;
}
.aura-4 {
  background: radial-gradient(
    circle at center,
    rgba(var(--color-4), 1) 0,
    rgba(var(--color-4), 0) 50%
  );
  top: calc(50% - var(--circle-size) / 2 - 200px);
  left: calc(50% - var(--circle-size) / 2 - 400px);
  transform-origin: calc(50% + 220px) calc(50% + 100px);
  animation: moveInCircle 20s reverse infinite;
}

.cursor-aura {
  background: radial-gradient(
    circle at center,
    rgba(var(--cursor-color), 0.8) 0,
    rgba(var(--cursor-color), 0) 50%
  );
  position: absolute;
  width: 100%;
  height: 100%;
  top: -50%;
  left: -50%;
  opacity: 0.5;
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

@keyframes moveVertical {
  0% {
    transform: translateY(-50%);
  }
  50% {
    transform: translateY(50%);
  }
  100% {
    transform: translateY(-50%);
  }
}

@keyframes moveHorizontal {
  0% {
    transform: translateX(-50%) translateY(-10%);
  }
  50% {
    transform: translateX(50%) translateY(10%);
  }
  100% {
    transform: translateX(-50%) translateY(-10%);
  }
}
</style>
