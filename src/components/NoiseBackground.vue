<script setup lang="ts"></script>

<template>
  <!-- Content -->
  <div class="aura-container">
    <div class="aura aura-1"></div>
    <div class="aura aura-2"></div>
  </div>

  <!-- Filter -->
  <svg xmlns="http://www.w3.org/2000/svg">
    <defs>
      <filter id="bgNoiseFilter">
        <!-- Blur -->
        <feGaussianBlur in="SourceGraphic" stdDeviation="25" result="blur" />
        <!-- Noise -->
        <feTurbulence type="fractalNoise" baseFrequency="0.7" numOctaves="3" result="turbulence" />
        <!-- Blend -->
        <feComposite in="blur" in2="turbulence" operator="in" />
      </filter>
    </defs>
  </svg>
</template>

<style scoped>
svg {
  display: none;
}

.aura-container {
  filter: url(#bgNoiseFilter);
  width: 100%;
  height: 100%;
}

.aura {
  position: absolute;
  width: var(--static-circle-size);
  height: var(--static-circle-size);
  border-radius: 50%;
  mix-blend-mode: hard-light;
}

.aura-1 {
  top: calc(57% - var(--static-circle-size) / 2);
  right: calc(35% - var(--static-circle-size) / 2);
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-middle-blue-green), 1) 50%,
    rgba(var(--rgb-maximum-blue-purple), 1) 100%
  );
  opacity: 1;
}

.aura-2 {
  top: calc(52% - var(--static-circle-size) / 2);
  right: calc(30% - var(--static-circle-size) / 2);
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-pale-magenta), 1) 5%,
    rgba(var(--rgb-maximum-blue-purple), 1) 100%
  );
  opacity: 0.8;
}
</style>
