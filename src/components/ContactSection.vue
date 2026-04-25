<script setup>
import { ref } from 'vue'

const wayImages = [
  new URL('../assets/img/way1.webp', import.meta.url).href,
  new URL('../assets/img/way2.webp', import.meta.url).href,
  new URL('../assets/img/way3.webp', import.meta.url).href,
]

const current = ref(0)

function prev() {
  current.value = (current.value - 1 + wayImages.length) % wayImages.length
}
function next() {
  current.value = (current.value + 1) % wayImages.length
}
function goTo(i) {
  current.value = i
}
</script>

<template>
  <section class="contact" id="contact">
    <div class="container">

      <div class="section-header">
        <h2>📍 Зв'язатися з нами</h2>
        <div class="divider"></div>
      </div>

      <div class="contact-layout">

        <!-- LEFT: info card + map -->
        <div class="contact-left">

          <!-- Styled info card -->
          <div class="info-card">
            <div class="info-card-glow"></div>

            <div class="info-group">
              <span class="info-label">
                <svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/></svg>
                Адреса
              </span>
              <p>м. Чугуїв, вул. Гвардійська, 4</p>
            </div>

            <div class="info-divider"></div>

            <div class="info-group">
              <span class="info-label">
                <svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/></svg>
                Телефон
              </span>
              <a href="tel:+380501376086" class="phone-link">+38 (050) 137-60-86</a>
              <a href="tel:+380509697892" class="phone-link">+38 (050) 969-78-92</a>
              <a href="tel:+380679137993" class="phone-link">+38 (067) 913-79-93</a>
            </div>

            <div class="info-divider"></div>

            <div class="info-group">
              <span class="info-label">
                <svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
                Графік роботи
              </span>
              <p class="hours">щоденно <strong>08:00 – 14:00</strong></p>
            </div>
          </div>

          <!-- Google Map -->
          <div class="map-wrapper">
            <iframe
              title="Стройматериалы Чугуев на карте"
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3320.316007656229!2d36.69360879999999!3d49.839429599999995!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x412715c832bfcef1%3A0x86be294e9bcaf35!2z0IQt0JLQhtCU0J3QntCS0JvQldCd0J3QryDQsdGD0LTRltCy0LXQu9GM0L3QuNC5INC80LDQs9Cw0LfQuNC9INCn0YPQs9GD0ZfQsg!5e1!3m2!1sru!2ssk!4v1777141954589!5m2!1sru!2ssk"
              allowfullscreen=""
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
            ></iframe>
          </div>
        </div>

        <!-- RIGHT: way carousel -->
        <div class="contact-right">

          <div class="carousel">
            <button class="carousel-btn prev" @click="prev" aria-label="Попередній">
              <svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M15 19l-7-7 7-7"/></svg>
            </button>

            <div class="carousel-track">
              <transition name="slide" mode="out-in">
                <img
                  :key="current"
                  :src="wayImages[current]"
                  :alt="`Фото дороги ${current + 1}`"
                  class="carousel-img"
                />
              </transition>
            </div>

            <button class="carousel-btn next" @click="next" aria-label="Наступний">
              <svg fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M9 5l7 7-7 7"/></svg>
            </button>

            <div class="carousel-dots">
              <button
                v-for="(img, i) in wayImages"
                :key="i"
                class="dot"
                :class="{ active: i === current }"
                @click="goTo(i)"
                :aria-label="`Фото ${i + 1}`"
              ></button>
            </div>

            <div class="carousel-counter">{{ current + 1 }} / {{ wayImages.length }}</div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
.contact {
  padding: 6rem 0;
  background-color: var(--c-dark);
}

.section-header {
  text-align: center;
  margin-bottom: 3.5rem;
}

.section-header h2 {
  font-size: clamp(2rem, 4vw, 2.8rem);
  margin-bottom: 1rem;
}

.divider {
  height: 4px;
  width: 60px;
  background-color: var(--c-primary);
  margin: 0 auto;
  border-radius: 2px;
}

/* ── Layout ── */
.contact-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: start;
}

@media (max-width: 900px) {
  .contact-layout { grid-template-columns: 1fr; }
}

.contact-left {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

/* ── Info card ── */
.info-card {
  position: relative;
  background: linear-gradient(135deg, rgba(21, 29, 48, 0.95) 0%, rgba(30, 40, 65, 0.9) 100%);
  border: 1px solid rgba(255, 138, 0, 0.2);
  border-radius: 1.25rem;
  padding: 2rem 2rem 1.5rem;
  backdrop-filter: blur(12px);
  overflow: hidden;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4), inset 0 1px 0 rgba(255,255,255,0.05);
}

/* Ambient glow in the top-right corner */
.info-card-glow {
  position: absolute;
  top: -40px;
  right: -40px;
  width: 160px;
  height: 160px;
  background: radial-gradient(circle, rgba(255, 138, 0, 0.18) 0%, transparent 70%);
  pointer-events: none;
}

.info-group {
  margin-bottom: 0;
}

.info-label {
  display: flex;
  align-items: center;
  gap: 0.45rem;
  font-size: 0.78rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--c-primary);
  margin-bottom: 0.5rem;
  font-family: var(--font-sans);
}

.info-label svg {
  width: 14px;
  height: 14px;
  flex-shrink: 0;
}

.info-group p {
  font-size: 1.1rem;
  font-weight: 500;
  color: var(--c-light);
  padding-left: 0.1rem;
}

.hours strong {
  color: var(--c-primary);
}

.info-divider {
  height: 1px;
  background: rgba(255,255,255,0.07);
  margin: 1.25rem 0;
}

.phone-link {
  display: block;
  font-size: 1.1rem;
  font-weight: 500;
  color: var(--c-light);
  text-decoration: none;
  margin-bottom: 0.3rem;
  padding-left: 0.1rem;
  transition: color var(--t-base);
}

.phone-link:hover {
  color: var(--c-primary);
}

/* ── Map ── */
.map-wrapper {
  border-radius: 1.25rem;
  overflow: hidden;
  border: 1px solid var(--c-gray-border);
  box-shadow: 0 10px 30px rgba(0,0,0,0.4);
}

.map-wrapper iframe {
  width: 100%;
  height: 300px;
  border: none;
  display: block;
  filter: brightness(0.85) contrast(1.1) saturate(0.9);
}

/* ── Right column ── */
.contact-right {
  display: flex;
  flex-direction: column;
  position: sticky;
  top: 2rem;
}

.way-label {
  font-family: var(--font-heading);
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: var(--c-light);
}

/* ── Carousel ── */
.carousel {
  position: relative;
  border-radius: 1.25rem;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0,0,0,0.5);
  border: 1px solid var(--c-gray-border);
}

.carousel-track {
  width: 100%;
  aspect-ratio: 4/3;
  background-color: var(--c-dark);
  overflow: hidden;
}

.carousel-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.slide-enter-active,
.slide-leave-active {
  transition: opacity 0.4s ease, transform 0.4s ease;
}
.slide-enter-from { opacity: 0; transform: translateX(30px); }
.slide-leave-to   { opacity: 0; transform: translateX(-30px); }

.carousel-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 10;
  width: 42px; height: 42px;
  background: rgba(11,17,33,0.75);
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

.carousel-btn svg { width: 18px; height: 18px; }
.prev { left: 0.75rem; }
.next { right: 0.75rem; }

.carousel-dots {
  position: absolute;
  bottom: 0.75rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 0.5rem;
}

.dot {
  width: 8px; height: 8px;
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
  top: 0.75rem; right: 0.75rem;
  background: rgba(11,17,33,0.7);
  color: var(--c-gray);
  font-size: 0.8rem;
  padding: 0.2rem 0.6rem;
  border-radius: 999px;
}
</style>
