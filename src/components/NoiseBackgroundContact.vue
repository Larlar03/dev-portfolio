<script setup lang="ts"></script>

<template>
  <!-- Content -->
  <div class="aura-container">
    <div id="heart"></div>
  </div>

  <!-- Filter -->
  <svg xmlns="http://www.w3.org/2000/svg">
    <defs>
      <filter id="heartNoiseFilter">
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
  filter: url(#heartNoiseFilter);
  width: 100%;
  height: 100%;
}

#heart {
  display: inline-block;
  height: var(--heart-size);
  margin: 0 10px;
  position: absolute;
  top: -275px;
  left: 175px;
  transform: rotate(80deg);
  width: var(--heart-size);
  /* mix-blend-mode: hard-light; */
  background: linear-gradient(
    85deg,
    rgba(var(--rgb-shampoo-pink), 1) 0%,
    rgba(var(--rgb-maximum-blue-purple), 1) 100%
  );
  opacity: 1;
}

#heart:before,
#heart:after {
  content: '';
  border-radius: var(--heart-border-radius);
  height: var(--heart-size);
  position: absolute;
  width: var(--heart-size);
}

#heart:before {
  top: -145px;
  left: 0;
  background: linear-gradient(
    -120deg,
    rgba(var(--rgb-pale-lavender), 1) 0%,
    rgba(var(--rgb-middle-blue-green), 1) 100%
  );
  opacity: 1;
}

#heart:after {
  left: 145px;
  top: 0;
  background: linear-gradient(
    62deg,
    rgba(var(--rgb-pale-lavender), 1) 0%,
    rgba(var(--rgb-pale-cornflower-blue), 1) 100%
  );
}

@media (min-width: 768px) {
  #heart {
    top: -375px;
    left: 450px;
    transform: rotate(80deg);
  }
}
</style>

/* background-color: #8EC5FC; background-image: linear-gradient(62deg, #8EC5FC 0%, #E0C3FC 100%); */
