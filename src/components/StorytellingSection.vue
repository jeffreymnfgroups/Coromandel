<script setup>
import { ref, onMounted } from 'vue'
import img15 from '@/assets/1 (15).webp'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.15 }
  )
  observer.observe(sectionRef.value)
})
</script>

<template>
  <section class="story section-hidden" :class="{ 'section-visible': visible }" id="story" ref="sectionRef">
    <div class="story__inner container">
      
      <div class="story__content">
        <p class="story__label">The Bigger Picture</p>
        <h2 class="story__heading">
          Why This Changes Everything<br><em>for a Local Business</em>
        </h2>

        <div class="story__body">
          <p>
            Your customers are deciding right now. From noticing your shop to searching on their phones, that critical 60-second window determines if they call you or forget you.
          </p>
          <ul class="story__list">
            <li><span class="story__bullet"></span> <strong>Keyword-aligned Google Profile:</strong> Let them find you instantly.</li>
            <li><span class="story__bullet"></span> <strong>Consistent Review Growth:</strong> Build undeniable trust naturally.</li>
            <li><span class="story__bullet"></span> <strong>24/7 Website Presence:</strong> Capture leads even while you sleep.</li>
          </ul>
          <p class="story__highlight">
            That's the gap we work on.
          </p>
        </div>

        <div class="story__closing">
          <svg class="story__closing-icon" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22c5.523 0 10-4.477 10-10S17.523 2 12 2 2 6.477 2 12s4.477 10 10 10z"/><path d="M12 6v6l4 2"/></svg>
          <p>
            You don't need to be the biggest. You just need to look like the <strong>most trustworthy</strong> when it counts.
          </p>
        </div>
      </div>

      <div class="story__visual">
        <div class="story__image-wrapper">
          <img :src="img15" alt="Local business analytics" class="story__img" />
          <div class="story__image-overlay"></div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.story {
  background-color: var(--color-bg);
  padding-block: var(--section-padding);
  position: relative;
  overflow: hidden;
}

.story::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-border), transparent);
}

.story__inner {
  display: grid;
  grid-template-columns: 1fr;
  gap: 3rem;
  align-items: center;
}

.story__content {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.story__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.story__label::before {
  content: '';
  display: inline-block;
  width: 1.5rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.story__heading {
  font-family: var(--font-display);
  font-size: clamp(2.25rem, 5vw, 3.5rem);
  font-weight: 400;
  line-height: 1.1;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.story__heading em {
  font-style: italic;
  color: var(--color-primary);
}

.story__body {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.story__body p {
  font-size: clamp(0.9375rem, 1.5vw, 1.0625rem);
  font-weight: 300;
  line-height: 1.8;
  color: var(--color-muted);
}

.story__list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.story__list li {
  font-size: 0.95rem;
  font-weight: 300;
  color: var(--color-muted);
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  line-height: 1.6;
}

.story__list strong {
  color: var(--color-text);
  font-weight: 500;
}

.story__bullet {
  margin-top: 0.4rem;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background-color: var(--color-gold);
  flex-shrink: 0;
  box-shadow: 0 0 8px rgba(201, 169, 110, 0.6);
}

.story__highlight {
  font-family: var(--font-display);
  font-style: italic;
  font-size: clamp(1.25rem, 2.5vw, 1.75rem) !important;
  font-weight: 400 !important;
  color: var(--color-primary) !important;
  padding-block: 0.5rem;
}

.story__closing {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1.5rem;
  border: 1px solid rgba(201, 169, 110, 0.25);
  background: linear-gradient(135deg, #111 0%, #0d0d0d 50%, #111 100%);
  margin-top: 1rem;
  text-align: left;
  border-radius: 4px;
}

.story__closing-icon {
  flex-shrink: 0;
  color: var(--color-gold);
  margin-top: 0.2rem;
}

.story__closing p {
  font-size: 0.95rem;
  font-weight: 300;
  line-height: 1.6;
  color: var(--color-muted);
}

.story__closing strong {
  color: var(--color-primary);
  font-weight: 400;
}

/* =============================================
   Visual Image
   ============================================= */
.story__visual {
  width: 100%;
  padding-block: 2rem;
}

.story__image-wrapper {
  position: relative;
  width: 100%;
  aspect-ratio: 4 / 3;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0,0,0,0.4);
  transform: translateZ(0); /* For hardware accel / rounded corners bug */
}

.story__img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  filter: brightness(0.9) contrast(1.1);
}

.story__image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(201, 169, 110, 0.2) 0%, transparent 50%, rgba(0, 0, 0, 0.4) 100%);
  pointer-events: none;
  transition: opacity 0.5s ease;
  opacity: 0.7;
}

.story__image-wrapper:hover .story__img {
  transform: scale(1.05);
}

.story__image-wrapper:hover .story__image-overlay {
  opacity: 1;
}

/* Float animation for the whole visual container */
@keyframes float {
  0% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
  100% { transform: translateY(0px); }
}

.section-visible .story__visual {
  animation: float 6s ease-in-out infinite;
}

/* =============================================
   Responsive
   ============================================= */
@media (min-width: 992px) {
  .story__inner {
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
  }
}
</style>
