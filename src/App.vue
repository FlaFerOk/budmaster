<script setup>
import HeroSection from './components/HeroSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>

<template>
  <main>
    <HeroSection />

    <div class="section-sep">
      <div class="sep-line"></div>
      <div class="sep-diamond"></div>
      <div class="sep-line"></div>
    </div>

    <FeaturesSection />

    <div class="section-sep">
      <div class="sep-line"></div>
      <div class="sep-diamond"></div>
      <div class="sep-line"></div>
    </div>

    <ContactSection />

    <div class="section-sep">
      <div class="sep-line"></div>
      <div class="sep-diamond"></div>
      <div class="sep-line"></div>
    </div>

    <FooterSection />
  </main>
</template>

<style>
.section-sep {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
  background-color: var(--c-dark);
}

.sep-line {
  flex: 1;
  height: 1px;
  background: linear-gradient(to right, transparent, rgba(255, 138, 0, 0.3), transparent);
}

.sep-diamond {
  width: 10px;
  height: 10px;
  background-color: var(--c-primary);
  transform: rotate(45deg);
  margin: 0 1rem;
  flex-shrink: 0;
  box-shadow: 0 0 10px rgba(255, 138, 0, 0.6);
}
</style>
