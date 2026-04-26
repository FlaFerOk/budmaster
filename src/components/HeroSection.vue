<script setup>
</script>

<template>
  <section class="hero" id="home">
    <div class="hero-overlay"></div>
    <div class="container hero-content">
      <h1 class="animate-fade-up">Ваш Надійний <br><span class="text-primary">Будівельний Партнер</span></h1>
      <p class="hero-subtitle animate-fade-up delay-100">Чугуїв • Е-ВІДНОВЛЕННЯ</p>
      
      <div class="hero-actions animate-fade-up delay-200">
        <a href="#contact" class="btn btn-primary">Зв'язатися з нами</a>
        <a href="#about" class="btn btn-outline">Дізнатися більше</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  background-image: url('/hero_background.png');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  padding-top: var(--header-height);
}

.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    135deg,
    rgba(11, 17, 33, 0.9) 0%,
    rgba(11, 17, 33, 0.7) 50%,
    rgba(21, 29, 48, 0.8) 100%
  );
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
  text-align: center;
  max-width: 800px;
}

h1 {
  font-size: clamp(2.5rem, 5vw, 4.5rem);
  margin-bottom: 1.5rem;
  letter-spacing: -0.02em;
}

.hero-subtitle {
  font-size: clamp(1.2rem, 3vw, 1.5rem);
  color: var(--c-gray);
  margin-bottom: 2.5rem;
  font-weight: 500;
  letter-spacing: 0.1em;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}
</style>
