<script setup>
import { ref, onMounted } from 'vue'
import img1 from '@/assets/1 (1).webp'
import img2 from '@/assets/1 (2).webp'
import img3 from '@/assets/1 (3).webp'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.15 }
  )
  observer.observe(sectionRef.value)
})

const steps = [
  {
    number: '01',
    title: 'Free Discovery Call',
    desc: 'We understand your business, your area, and your goals. No pressure, no jargon.',
    // Replace with your own images
    image: img1,
    imageAlt: 'Professional discovery call',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.21 12a19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/></svg>`,
  },
  {
    number: '02',
    title: 'We Build Your Local Visibility System',
    desc: 'Google profile optimization, keyword research, QR codes, review system, and website — set up properly and ready to work.',
    image: img2,
    imageAlt: 'Local SEO and business visibility setup',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M12 20V10"/><path d="M18 20V4"/><path d="M6 20v-4"/></svg>`,
  },
  {
    number: '03',
    title: 'You Start Getting More Enquiries',
    desc: 'Your business becomes easier to find, easier to trust, and easier to contact. We handle the technical side. You focus on serving your customers.',
    image: img3,
    imageAlt: 'Business growth and customer enquiries',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>`,
  },
]
</script>

<template>
  <section
    class="how section-hidden"
    :class="{ 'section-visible': visible }"
    id="how-it-works"
    ref="sectionRef"
  >
    <div class="how__inner container">

      <div class="how__header">
        <p class="how__label">How It Works</p>
        <h2 class="how__heading">
          Three Simple Steps<br><em>to Get Started</em>
        </h2>
      </div>

      <div class="how__grid">
        <div
          v-for="(step, index) in steps"
          :key="step.number"
          class="step-card"
          :style="{ '--delay': `${index * 120}ms` }"
        >
          <!-- Image Panel -->
          <div class="step-card__image-wrap">
            <img
              :src="step.image"
              :alt="step.imageAlt"
              class="step-card__image"
              loading="lazy"
            />
            <!-- Gradient overlay -->
            <div class="step-card__image-overlay" aria-hidden="true"></div>
            <!-- Step number floats over image -->
            <span class="step-card__number" aria-hidden="true">{{ step.number }}</span>
          </div>

          <!-- Body -->
          <div class="step-card__body">
            <div class="step-card__icon-row">
              <span class="step-card__icon" v-html="step.icon" aria-hidden="true"></span>
              <span class="step-card__icon-line" aria-hidden="true"></span>
            </div>
            <h3 class="step-card__title">{{ step.title }}</h3>
            <p class="step-card__desc">{{ step.desc }}</p>
          </div>

          <!-- Hover top border glow -->
          <div class="step-card__glow" aria-hidden="true"></div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
/* ─── Section ───────────────────────────────────────── */
.how {
  background-color: var(--color-surface);
  padding-block: var(--section-padding);
  position: relative;
}

.how::before {
  content: '';
  position: absolute;
  inset: 0;
  top: auto;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-border), transparent);
}

/* ─── Header ─────────────────────────────────────────── */
.how__header {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  margin-bottom: clamp(3rem, 6vw, 5rem);
  text-align: center;
  align-items: center;
}

.how__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.how__label::before,
.how__label::after {
  content: '';
  display: inline-block;
  width: 1.5rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.how__heading {
  font-family: var(--font-display);
  font-size: clamp(2.25rem, 5vw, 3.75rem);
  font-weight: 400;
  line-height: 1.1;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.how__heading em {
  font-style: italic;
  color: var(--color-primary);
}

/* ─── Grid ───────────────────────────────────────────── */
.how__grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
}

@media (min-width: 768px) {
  .how__grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* ─── Card ───────────────────────────────────────────── */
.step-card {
  display: flex;
  flex-direction: column;
  border: 1px solid var(--color-border);
  background-color: var(--color-bg);
  position: relative;
  overflow: hidden;
  transition: border-color 0.35s ease, transform 0.35s ease, box-shadow 0.35s ease;
}

.step-card:hover {
  border-color: rgba(201, 169, 110, 0.4);
  transform: translateY(-4px);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.35);
}

/* ─── Top glow bar (replaces ::before) ──────────────── */
.step-card__glow {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(to right, var(--color-gold), transparent);
  opacity: 0;
  transition: opacity 0.35s ease;
  z-index: 3;
}

.step-card:hover .step-card__glow {
  opacity: 1;
}

/* ─── Image Panel ────────────────────────────────────── */
.step-card__image-wrap {
  position: relative;
  width: 100%;
  aspect-ratio: 16 / 9;
  overflow: hidden;
}

.step-card__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.55s ease, filter 0.55s ease;
  filter: grayscale(30%) brightness(0.75);
}

.step-card:hover .step-card__image {
  transform: scale(1.06);
  filter: grayscale(0%) brightness(0.85);
}

/* Dark + gold gradient over image */
.step-card__image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    160deg,
    rgba(0, 0, 0, 0.15) 0%,
    rgba(0, 0, 0, 0.55) 70%,
    rgba(10, 8, 5, 0.88) 100%
  );
  z-index: 1;
}

/* Step number floated bottom-right of image */
.step-card__number {
  position: absolute;
  bottom: 0.85rem;
  right: 1.1rem;
  font-family: var(--font-display);
  font-size: 3.5rem;
  font-weight: 400;
  line-height: 1;
  letter-spacing: -0.03em;
  color: rgba(201, 169, 110, 0.22);
  z-index: 2;
  transition: color 0.35s ease;
  user-select: none;
}

.step-card:hover .step-card__number {
  color: rgba(201, 169, 110, 0.4);
}

/* ─── Card Body ─────────────────────────────────────── */
.step-card__body {
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
  padding: clamp(1.5rem, 2.5vw, 2.25rem);
  flex: 1;
}

/* Icon row with decorative line */
.step-card__icon-row {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.step-card__icon {
  color: var(--color-gold);
  opacity: 0.85;
  display: flex;
  align-items: center;
  flex-shrink: 0;
  transition: opacity 0.3s ease;
}

.step-card:hover .step-card__icon {
  opacity: 1;
}

.step-card__icon-line {
  flex: 1;
  height: 1px;
  background: linear-gradient(to right, rgba(201, 169, 110, 0.3), transparent);
}

/* Title */
.step-card__title {
  font-family: var(--font-display);
  font-size: 1.275rem;
  font-weight: 400;
  color: var(--color-text);
  line-height: 1.25;
  transition: color 0.3s ease;
  margin: 0;
}

.step-card:hover .step-card__title {
  color: var(--color-primary);
}

/* Description */
.step-card__desc {
  font-size: 0.875rem;
  font-weight: 300;
  line-height: 1.75;
  color: var(--color-muted);
  margin: 0;
}
</style>
