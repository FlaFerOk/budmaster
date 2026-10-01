<script setup>
import { ref } from 'vue'

// Carousel images: img1..img6
const images = [
  new URL('../assets/img/img1.webp', import.meta.url).href,
  new URL('../assets/img/img2.webp', import.meta.url).href,
  new URL('../assets/img/img3.webp', import.meta.url).href,
  new URL('../assets/img/img4.webp', import.meta.url).href,
  new URL('../assets/img/img5.webp', import.meta.url).href,
  new URL('../assets/img/img6.webp', import.meta.url).href,
]

const current = ref(0)

function prev() {
  current.value = (current.value - 1 + images.length) % images.length
}
function next() {
  current.value = (current.value + 1) % images.length
}
function goTo(i) {
  current.value = i
}

const features = [
  {
    icon: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 002-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"></path></svg>`,
    title: 'Широкий асортимент',
    items: ['від цементу до лакофарбових матеріалів', 'від гіпсокартону до покрівлі']
  },
  {
    icon: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>`,
    title: 'Доставка по місту та району',
    items: ['швидко', 'надійно', 'з гарантією']
  },
  {
    icon: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>`,
    title: 'Ціни від виробника',
    items: ['оплата через термінал', 'оплата готівкою', 'на картку', 'по перерахунку', 'через Е-Відновлення']
  },
  {
    icon: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8h2a2 2 0 012 2v6a2 2 0 01-2 2h-2v4l-4-4H9a1.994 1.994 0 01-1.414-.586m0 0L11 14h4a2 2 0 002-2V6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2v4l.586-.586z"></path></svg>`,
    title: 'Консультація від фахівця',
    items: ['допоможемо підібрати все для вашого проєкту.']
  },
  {
    icon: `<svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2 7h18v1a2 2 0 01-2 2H4a2 2 0 01-2-2V7zM13 10v7.5l2.5 2.5H21M17 10v6l1 1h3M6 2v2M10 2v2M14 2v2"></path></svg>`,
    title: 'Водостічні системи Rainway',
    items: ['сухі стіни в будь-яку зливу', 'елементи збираються як Lego', 'весь комплект на складі — забирай та став']
  }
]
</script>

<template>
  <section class="about" id="about">
    <div class="container">

      <!-- Section header -->
      <div class="section-header">
        <h2>Про нас</h2>
        <div class="divider"></div>
        <p class="section-sub">Ми — ваш надійний постачальник будівельних матеріалів у Чугуєві.<br>
          Маємо в наявності водостічні системи <span class="text-primary">Rainway</span>.<br>
          Працюємо з програмою <span class="text-primary">Е-Відновлення</span>.
        </p>
      </div>

      <!-- Photo carousel -->
      <div class="carousel">
        <button class="carousel-btn prev" @click="prev" aria-label="Previous">
          <svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M15 19l-7-7 7-7"/></svg>
        </button>

        <div class="carousel-track">
          <transition name="slide" mode="out-in">
            <img
              :key="current"
              :src="images[current]"
              :alt="`Фото ${current + 1}`"
              class="carousel-img"
            />
          </transition>
        </div>

        <button class="carousel-btn next" @click="next" aria-label="Next">
          <svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M9 5l7 7-7 7"/></svg>
        </button>

        <!-- Dots -->
        <div class="carousel-dots">
          <button
            v-for="(img, i) in images"
            :key="i"
            class="dot"
            :class="{ active: i === current }"
            @click="goTo(i)"
            :aria-label="`Фото ${i + 1}`"
          ></button>
        </div>

        <div class="carousel-counter">{{ current + 1 }} / {{ images.length }}</div>
      </div>

      <!-- Features grid -->
      <div class="features-grid" style="">
        <div
          v-for="(feature, index) in features"
          :key="index"
          class="feature-card"
        >
          <div class="icon-wrapper" v-html="feature.icon"></div>
          <h3>{{ feature.title }}</h3>
          <ul>
            <li v-for="(item, i) in feature.items" :key="i">
              <span class="bullet"></span>
              {{ item }}
            </li>
          </ul>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.about {
  padding: 6rem 0;
  background-color: var(--c-dark-soft);
}

.section-header {
  text-align: center;
  margin-bottom: 3.5rem;
}

.section-header h2 {
  font-size: clamp(2rem, 4vw, 2.8rem);
  margin-bottom: 1rem;
}

.section-sub {
  color: var(--c-gray);
  max-width: 600px;
  margin: 1rem auto 0;
  font-size: 1.05rem;
}

.divider {
  height: 4px;
  width: 60px;
  background-color: var(--c-primary);
  margin: 0 auto;
  border-radius: 2px;
}

/* ── Carousel ── */
.carousel {
  position: relative;
  width: 100%;
  max-width: 900px;
  margin: 0 auto 4rem;
  border-radius: 1.25rem;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0,0,0,0.5);
}

.carousel-track {
  width: 100%;
  aspect-ratio: 16/9;
  background-color: var(--c-dark);
  overflow: hidden;
}

.carousel-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* Slide transition */
.slide-enter-active,
.slide-leave-active {
  transition: opacity 0.4s ease, transform 0.4s ease;
}
.slide-enter-from {
  opacity: 0;
  transform: translateX(30px);
}
.slide-leave-to {
  opacity: 0;
  transform: translateX(-30px);
}

.carousel-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 10;
  width: 46px;
  height: 46px;
  background: rgba(11, 17, 33, 0.75);
  border: 1px solid var(--c-gray-border);
  color: var(--c-light);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: background var(--t-base), border-color var(--t-base);
}

.carousel-btn:hover {
  background: var(--c-primary);
  border-color: var(--c-primary);
}

.carousel-btn svg {
  width: 20px;
  height: 20px;
}

.prev { left: 1rem; }
.next { right: 1rem; }

.carousel-dots {
  position: absolute;
  bottom: 1rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 0.5rem;
}

.dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: rgba(255,255,255,0.4);
  border: none;
  cursor: pointer;
  transition: background var(--t-base), transform var(--t-base);
}

.dot.active {
  background: var(--c-primary);
  transform: scale(1.35);
}

.carousel-counter {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(11, 17, 33, 0.7);
  color: var(--c-gray);
  font-size: 0.8rem;
  padding: 0.2rem 0.6rem;
  border-radius: 999px;
  font-family: var(--font-sans);
}

/* ── Features grid ── */
.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 2rem;
}

.feature-card {
  background-color: var(--c-dark);
  padding: 2.5rem 2rem;
  border-radius: 1rem;
  border: 1px solid var(--c-gray-border);
  transition: all var(--t-base);
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.feature-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 4px;
  background-color: var(--c-primary);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform var(--t-base);
}

.feature-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0,0,0,0.5);
  border-color: rgba(255,138,0,0.3);
}

.feature-card:hover::before { transform: scaleX(1); }

.icon-wrapper {
  width: 60px; height: 60px;
  background-color: rgba(255,138,0,0.1);
  color: var(--c-primary);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
  transition: all var(--t-base);
}

.icon-wrapper :deep(svg) { width: 30px; height: 30px; }

.feature-card:hover .icon-wrapper {
  background-color: var(--c-primary);
  color: #fff;
}

h3 {
  font-size: 1.25rem;
  margin-bottom: 1rem;
  color: var(--c-light);
}

ul { list-style: none; }

li {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  gap: 0.75rem;
  margin-bottom: 0.5rem;
  color: var(--c-gray);
  font-size: 0.95rem;
}

.bullet {
  margin-top: 0.4rem;
  min-width: 6px; height: 6px;
  background-color: var(--c-primary);
  border-radius: 50%;
}
</style>
