<script setup>
import { ref, onMounted } from 'vue'
import img10 from '@/assets/1 (10).webp'
import img11 from '@/assets/1 (11).webp'
import img12 from '@/assets/1 (12).webp'
import img13 from '@/assets/1 (13).webp'
import img14 from '@/assets/1 (14).webp'
import img15 from '@/assets/1 (15).webp'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        visible.value = true
        observer.disconnect()
      }
    },
    { threshold: 0.1 }
  )
  observer.observe(sectionRef.value)
})

const audiences = [
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>`,
    title: 'Retail Shops',
    desc: 'More footfall and local discovery for your store.',
    image: img10,
    tag: 'Local Discovery',
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 12h-4l-3 9L9 3l-3 9H2"/></svg>`,
    title: 'Clinics & Healthcare',
    desc: 'Patients find and trust you faster online.',
    image: img11,
    tag: 'Patient Trust',
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M18 8h1a4 4 0 0 1 0 8h-1"/><path d="M2 8h16v9a4 4 0 0 1-4 4H6a4 4 0 0 1-4-4V8z"/>e x1="6" y1="1" x2="6" y2="4"/>e x1="10" y1="1" x2="10" y2="4"/>e x1="14" y1="1" x2="14" y2="4"/></svg>`,
    title: 'Restaurants & Food',
    desc: 'Appear in "near me" searches and attract more diners.',
    image: img12,
    tag: 'Near Me Searches',
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg>`,
    title: 'Salons & Beauty',
    desc: 'Grow reviews and bookings consistently.',
    image: img13,
    tag: 'Reviews & Bookings',
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/><path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/></svg>`,
    title: 'Coaching & Tutors',
    desc: 'Build local digital credibility for your institute.',
    image: img14,
    tag: 'Digital Credibility',
  },
  {
    icon: `<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"/></svg>`,
    title: 'Service Providers',
    desc: 'Electricians, plumbers, photographers — a stronger online presence.',
    image: img15,
    tag: 'Online Presence',
  },
]
</script>

<template>
  <section
    class="audience section-hidden"
    :class="{ 'section-visible': visible }"
    id="who-this-is-for"
    ref="sectionRef"
  >
    <div class="audience__inner container">

      <!-- Header -->
      <div class="audience__header">
        <p class="audience__label">Who This Is For</p>
        <h2 class="audience__heading">
          Coromandel Branding Solutions<br /><em>works best for</em>
        </h2>
        <p class="audience__subtext">
          Built specifically for local businesses that deserve to be found online.
        </p>
      </div>

      <!-- Cards Grid -->
      <div class="audience__grid">
        <article
          v-for="a in audiences"
          :key="a.title"
          class="a-card"
          :style="{ '--card-img': `url('${a.image}')` }"
        >
          <!-- Background image layer -->
          <div class="a-card__bg" aria-hidden="true"></div>

          <!-- Gradient overlay -->
          <div class="a-card__overlay" aria-hidden="true"></div>

          <!-- Content -->
          <div class="a-card__content">
            <span class="a-card__tag">{{ a.tag }}</span>
            <div class="a-card__bottom">
              <div class="a-card__icon" v-html="a.icon" aria-hidden="true"></div>
              <div class="a-card__text">
                <h3 class="a-card__title">{{ a.title }}</h3>
                <p class="a-card__desc">{{ a.desc }}</p>
              </div>
            </div>
          </div>
        </article>
      </div>

      <p class="audience__note">
        Any small business that knows their offline reputation should be stronger online too.
      </p>

    </div>
  </section>
</template>

<style scoped>
/* ─── Section ─────────────────────────────────────────────── */
.audience {
  background-color: var(--color-bg);
  padding-block: var(--section-padding);
  position: relative;
}

.audience::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-border), transparent);
}

/* ─── Header ──────────────────────────────────────────────── */
.audience__header {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: clamp(3rem, 6vw, 4.5rem);
  max-width: 640px;
}

.audience__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.audience__label::before {
  content: '';
  display: inline-block;
  width: 2rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.audience__heading {
  font-family: var(--font-display);
  font-size: clamp(2.25rem, 5vw, 3.75rem);
  font-weight: 400;
  line-height: 1.1;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.audience__heading em {
  font-style: italic;
  color: var(--color-primary);
}

.audience__subtext {
  font-size: 0.9375rem;
  font-weight: 300;
  color: var(--color-muted);
  line-height: 1.6;
}

/* ─── Grid ────────────────────────────────────────────────── */
.audience__grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5px;
  background-color: var(--color-border);
  border: 1.5px solid var(--color-border);
  border-radius: 4px;
  overflow: hidden;
}

@media (min-width: 640px) {
  .audience__grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (min-width: 1024px) {
  .audience__grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* ─── Card ────────────────────────────────────────────────── */
.a-card {
  position: relative;
  min-height: 260px;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  overflow: hidden;
  cursor: default;
}

/* Background image */
.a-card__bg {
  position: absolute;
  inset: 0;
  background-image: var(--card-img);
  background-size: cover;
  background-position: center;
  transition: transform 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94),
              filter 0.6s ease;
  filter: grayscale(40%) brightness(0.55);
}

.a-card:hover .a-card__bg {
  transform: scale(1.06);
  filter: grayscale(10%) brightness(0.45);
}

/* Gradient overlay */
.a-card__overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.88) 0%,
    rgba(0, 0, 0, 0.4) 50%,
    rgba(0, 0, 0, 0.05) 100%
  );
  transition: opacity 0.4s ease;
}

.a-card:hover .a-card__overlay {
  background: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.92) 0%,
    rgba(0, 0, 0, 0.55) 55%,
    rgba(0, 0, 0, 0.1) 100%
  );
}

/* Content sits above overlays */
.a-card__content {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: clamp(1.25rem, 2.5vw, 1.75rem);
}

/* Tag — top-left badge */
.a-card__tag {
  align-self: flex-start;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--color-gold);
  background: rgba(0, 0, 0, 0.45);
  border: 1px solid rgba(var(--color-gold-rgb, 200, 160, 80), 0.35);
  padding: 0.3rem 0.65rem;
  border-radius: 2px;
  backdrop-filter: blur(4px);
  opacity: 0;
  transform: translateY(-6px);
  transition: opacity 0.35s ease 0.05s, transform 0.35s ease 0.05s;
}

.a-card:hover .a-card__tag {
  opacity: 1;
  transform: translateY(0);
}

/* Bottom section: icon + text */
.a-card__bottom {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}

.a-card__icon {
  color: var(--color-gold);
  flex-shrink: 0;
  opacity: 0.9;
  transition: opacity 0.3s ease, transform 0.3s ease;
  margin-top: 0.1rem;
}

.a-card:hover .a-card__icon {
  opacity: 1;
  transform: scale(1.1);
}

.a-card__text {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}

.a-card__title {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 400;
  color: #ffffff;
  transition: color 0.3s ease;
}

.a-card:hover .a-card__title {
  color: var(--color-gold);
}

.a-card__desc {
  font-size: 0.82rem;
  font-weight: 300;
  line-height: 1.65;
  color: rgba(255, 255, 255, 0.65);
  transition: color 0.3s ease;
}

.a-card:hover .a-card__desc {
  color: rgba(255, 255, 255, 0.82);
}

/* ─── Footer note ─────────────────────────────────────────── */
.audience__note {
  text-align: center;
  margin-top: 2.5rem;
  font-size: 0.9375rem;
  font-weight: 300;
  font-style: italic;
  color: var(--color-muted);
}

/* ─── Scroll animation ────────────────────────────────────── */
.section-hidden .a-card {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.55s ease, transform 0.55s ease;
}

.section-hidden .a-card:nth-child(1) { transition-delay: 0.05s; }
.section-hidden .a-card:nth-child(2) { transition-delay: 0.12s; }
.section-hidden .a-card:nth-child(3) { transition-delay: 0.19s; }
.section-hidden .a-card:nth-child(4) { transition-delay: 0.26s; }
.section-hidden .a-card:nth-child(5) { transition-delay: 0.33s; }
.section-hidden .a-card:nth-child(6) { transition-delay: 0.40s; }

.section-visible .a-card {
  opacity: 1;
  transform: translateY(0);
}
</style>
