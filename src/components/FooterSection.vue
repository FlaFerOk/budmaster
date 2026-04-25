<script setup>
</script>

<template>
  <footer class="footer">
    <div class="container text-center">
      <div class="footer-slogan">
        <span class="animate-fade-up">🧱 Обирайте якість.</span>
        <span class="animate-fade-up delay-100">Обирайте надійність.</span>
        <span class="text-primary animate-fade-up delay-200">Обирайте нас!</span>
      </div>
      <p class="copyright">© {{ new Date().getFullYear() }} Стройматериалы Чугуев. Всі права захищені.</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  padding: 4rem 0 2rem;
  background-color: var(--c-dark);
  border-top: 1px solid var(--c-gray-border);
}

.text-center {
  text-align: center;
}

.footer-slogan {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  font-family: var(--font-heading);
  font-size: clamp(1.5rem, 4vw, 2.5rem);
  font-weight: 700;
  margin-bottom: 3rem;
}

.copyright {
  color: var(--c-gray);
  font-size: 0.9rem;
}
</style>
