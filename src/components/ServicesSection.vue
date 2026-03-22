<script setup>
import { ref, onMounted } from 'vue'
import img16 from '@/assets/1 (16).webp'
import img17 from '@/assets/1 (17).webp'
import img2 from '@/assets/1 (2).webp'
import img4 from '@/assets/1 (4).webp'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.15 }
  )
  observer.observe(sectionRef.value)
})

const services = [
  {
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>`,
    title: 'Google Business Profile Optimization',
    description: 'Make your business easier to find on Google Maps and local search — so the right customers discover you first.',
    image: img16
  },
  {
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>`,
    title: 'Review Growth System',
    description: 'Collect more genuine reviews consistently with a simple, frictionless QR-based process.',
    image: img17
  },
  {
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>`,
    title: 'Local Business Website',
    description: 'Show your services, establish authority, and capture leads 24/7 — even while you sleep.',
    image: img2
  },
  {
    icon: `<svg width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>`,
    title: 'Keyword Research for Local SEO',
    description: 'Align your profile and website with the actual words your local customers search for.',
    image: img4
  },
]
</script>

<template>
  <section class="services section-hidden" :class="{ 'section-visible': visible }" id="services" ref="sectionRef">
    <div class="services__inner container">

      <!-- Header -->
      <div class="services__header">
        <p class="services__label">What We Do</p>
        <h2 class="services__heading">A Simple Growth System Built<br><em>for Local Businesses</em></h2>
        <p class="services__sub">
          We don't just "make websites" or "manage your Google profile." We build a
          Local Visibility System — a connected set of tools that work together to help
          your business get found, earn trust, and capture more enquiries every single day.
        </p>
      </div>

      <!-- Grid -->
      <div class="services__grid">
        <article
          v-for="service in services"
          :key="service.title"
          class="card"
        >
          <div class="card__bg-wrapper">
            <img :src="service.image" :alt="service.title" class="card__bg-img" />
            <div class="card__bg-overlay"></div>
          </div>
          <div class="card__content">
            <div class="card__icon" v-html="service.icon" aria-hidden="true"></div>
            <h3 class="card__title">{{ service.title }}</h3>
            <p class="card__desc">{{ service.description }}</p>
          </div>
          <div class="card__line" aria-hidden="true"></div>
        </article>
      </div>

    </div>
  </section>
</template>

<style scoped>
/* =============================================
   Section
   ============================================= */
.services {
  background-color: var(--color-surface);
  padding-block: var(--section-padding);
  position: relative;
}

/* Top edge fade from hero */
.services::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-border), transparent);
}

/* =============================================
   Header
   ============================================= */
.services__header {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  margin-bottom: clamp(3rem, 6vw, 5rem);
}

.services__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.services__label::before {
  content: '';
  display: inline-block;
  width: 2rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.services__heading {
  font-family: var(--font-display);
  font-size: clamp(2.25rem, 5vw, 3.75rem);
  font-weight: 400;
  line-height: 1.1;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.services__heading em {
  font-style: italic;
  color: var(--color-primary);
}

.services__sub {
  font-size: 0.9375rem;
  font-weight: 300;
  line-height: 1.8;
  color: var(--color-muted);
  max-width: 56ch;
}

/* =============================================
   Grid
   ============================================= */
.services__grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1px;
  background-color: var(--color-border);
  border: 1px solid var(--color-border);
}

/* =============================================
   Card
   ============================================= */
.card {
  position: relative;
  background-color: var(--color-surface);
  padding: clamp(1.75rem, 3vw, 2.75rem);
  display: flex;
  flex-direction: column;
  overflow: hidden;
  transition: background-color 0.3s ease;
  cursor: default;
  min-height: 280px;
}

/* Card Background Image & Overlays */
.card__bg-wrapper {
  position: absolute;
  inset: 0;
  z-index: 0;
  overflow: hidden;
  opacity: 1;
  transition: opacity 0.5s ease;
}

.card__bg-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transform: scale(1.1);
  transition: transform 0.6s cubic-bezier(0.2, 0.8, 0.2, 1);
  filter: grayscale(100%);
}

.card__bg-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(13, 13, 13, 0.95) 0%, rgba(13, 13, 13, 0.6) 100%);
}

.card__content {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  height: 100%;
}

/* Gold corner accent on hover */
.card::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(to right, var(--color-gold), transparent);
  transition: width 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 2;
}

.card:hover {
  background-color: #1a1a1a;
  transform: translateY(-2px);
  transition: background-color 0.3s ease, transform 0.3s ease;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}

.card:hover .card__bg-wrapper {
  opacity: 1;
}

.card:hover .card__bg-img {
  transform: scale(1);
}

.card:hover::after {
  width: 100%;
}

/* Bottom divider line — animates gold on hover */
.card__line {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 1px;
  background-color: transparent;
  transition: background-color 0.3s ease;
  z-index: 2;
}

.card:hover .card__line {
  background-color: rgba(201, 169, 110, 0.12);
}

/* Icon */
.card__icon {
  color: var(--color-gold);
  line-height: 1;
  opacity: 0.85;
  transition: opacity 0.3s ease, transform 0.3s ease, color 0.3s ease;
  margin-bottom: auto;
}

.card:hover .card__icon {
  opacity: 1;
  transform: scale(1.1);
  color: #fff;
}

/* Title */
.card__title {
  font-family: var(--font-display);
  font-size: 1.375rem;
  font-weight: 400;
  letter-spacing: 0.01em;
  color: var(--color-text);
  transition: color 0.3s ease;
}

.card:hover .card__title {
  color: var(--color-primary);
}

/* Description */
.card__desc {
  font-size: 0.95rem;
  font-weight: 300;
  line-height: 1.7;
  color: var(--color-muted);
  transition: color 0.3s ease;
}

.card:hover .card__desc {
  color: #e0e0e0;
}

/* =============================================
   Responsive
   ============================================= */
@media (min-width: 640px) {
  .services__grid {
    grid-template-columns: 1fr 1fr;
  }
}
</style>
