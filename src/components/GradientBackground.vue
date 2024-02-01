<script setup lang="ts"></script>

<template>
  <div id="gradient-background">
    <div id="aura-container">
      <div class="aura aura-1"></div>
      <div class="aura aura-2"></div>
      <div class="aura aura-3"></div>
      <div class="aura aura-4"></div>
    </div>
  </div>

  <!-- Filter Effects -->
  <svg xmlns="http://www.w3.org/2000/svg">
    <defs>
      <filter id="gradientBgFilter">
        <!-- Blur -->
        <feGaussianBlur in="SourceGraphic" stdDeviation="5" result="blur" />
        <!-- Noise -->
        <feTurbulence
          type="fractalNoise"
          baseFrequency="0.7"
          numOctaves="200"
          result="turbulence"
        />
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

#gradient-background {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  overflow: hidden;
  background-image: linear-gradient(
    77deg,
    var(--gradient-1) 0%,
    var(--gradient-2) 19%,
    var(--gradient-3) 39%,
    var(--gradient-4) 60%,
    var(--gradient-5) 80%,
    var(--gradient-6) 100%
  );
}

#aura-container {
  filter: url(#gradientBgFilter);
  width: 100%;
  height: 100%;
}

.aura {
  position: absolute;
  width: var(--circle-size);
  height: var(--circle-size);
  background-repeat: no-repeat;
  opacity: 1;
}

.aura-1 {
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-shampoo-pink), 1) 0,
    rgba(var(--rgb-shampoo-pink), 0) 45%
  );
  top: calc(25% - var(--circle-size) / 2);
  left: calc(-5% - var(--circle-size) / 2);
}

.aura-2 {
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-shampoo-pink), 1) 0,
    rgba(var(--rgb-shampoo-pink), 0) 50%
  );
  top: calc(-5% - var(--circle-size) / 2);
  left: calc(55% - var(--circle-size) / 2);
}
.aura-3 {
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-middle-blue-green), 1) 0,
    rgba(var(--rgb-middle-blue-green), 0) 50%
  );
  top: calc(80% - var(--circle-size) / 2);
  left: calc(80% - var(--circle-size) / 2);
}
.aura-4 {
  background: radial-gradient(
    circle at center,
    rgba(var(--rgb-blue-bell-purple), 1) 0,
    rgba(var(--rgb-blue-bell-purple), 0) 50%
  );
  top: calc(80% - var(--circle-size) / 2);
  left: calc(40% - var(--circle-size) / 2);
}
</style>
