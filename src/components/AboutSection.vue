<script setup>
import { ref, onMounted } from 'vue'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.15 }
  )
  observer.observe(sectionRef.value)
})

const painPoints = [
  {
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/><line x1="8" y1="11" x2="14" y2="11"/></svg>`,
    title: "You're hard to find",
    desc: 'Your Google profile is incomplete or invisible for key local searches.',
  },
  {
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>`,
    title: 'Your reviews are thin',
    desc: 'Fewer reviews make customers second-guess their choice.',
  },
  {
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>`,
    title: 'You have no website',
    desc: "Or the one you have doesn't explain anything clearly.",
  },
  {
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>`,
    title: 'Your information is scattered',
    desc: "Customers can't find your location, number, or services easily.",
  },
  {
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>`,
    title: 'Competitors look more professional',
    desc: 'So even if your service is better, they get the call first.',
  },
]
</script>

<template>
  <section class="about section-hidden" :class="{ 'section-visible': visible }" id="why-it-matters" ref="sectionRef">
    <div class="about__inner container">

      <!-- Left: copy -->
      <div class="about__content">
        <p class="about__label">Why This Matters</p>

        <h2 class="about__heading">
          Why Most Local Businesses Lose Customers Online —
          <em>Without Knowing It</em>
        </h2>

        <div class="about__body">
          <p>
            You might be the best in your area. But your customer doesn't know that yet.
            Before they visit, they search. Before they call, they check Google. Before
            they trust you, they look at your reviews, your photos, and your website.
          </p>
          <p>
            In that 30-second judgment, your business either wins the enquiry — or
            loses it to someone else. Here's what's quietly costing you customers right now:
          </p>
        </div>
      </div>

      <!-- Right: pain points -->
      <div class="about__grid">
        <div
          v-for="point in painPoints"
          :key="point.title"
          class="pain-card"
        >
          <div class="pain-card__icon" v-html="point.icon" aria-hidden="true"></div>
          <div class="pain-card__text">
            <h3 class="pain-card__title">{{ point.title }}</h3>
            <p class="pain-card__desc">{{ point.desc }}</p>
          </div>
        </div>
      </div>

    </div>

    <!-- Bottom message -->
    <div class="about__bottom container">
      <p class="about__conclusion">
        Your business may be excellent offline. But if it isn't presented clearly online,
        many customers will never give you the chance to prove it.
        <strong>That's the problem we solve.</strong>
      </p>
    </div>
  </section>
</template>

<style scoped>
/* =============================================
   Section
   ============================================= */
.about {
  background-color: var(--color-bg);
  padding-block: var(--section-padding);
  position: relative;
}

.about::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-border), transparent);
}

/* =============================================
   Layout
   ============================================= */
.about__inner {
  display: grid;
  grid-template-columns: 1fr;
  gap: clamp(3rem, 6vw, 5rem);
  align-items: start;
}

@media (min-width: 900px) {
  .about__inner {
    grid-template-columns: 1fr 1fr;
  }
}

/* =============================================
   Content (left)
   ============================================= */
.about__content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.about__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.about__label::before {
  content: '';
  display: inline-block;
  width: 2rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.about__heading {
  font-family: var(--font-display);
  font-size: clamp(2rem, 4vw, 3.25rem);
  font-weight: 400;
  line-height: 1.12;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.about__heading em {
  font-style: italic;
  color: var(--color-primary);
}

.about__body {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.about__body p {
  font-size: 0.9375rem;
  font-weight: 300;
  line-height: 1.8;
  color: var(--color-muted);
}

/* =============================================
   Pain Points Grid (right)
   ============================================= */
.about__grid {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.pain-card {
  display: flex;
  align-items: flex-start;
  gap: 1.25rem;
  padding: 1.5rem 1.25rem;
  border: 1px solid var(--color-border);
  border-bottom: none;
  background-color: var(--color-surface);
  transition: border-color 0.3s ease, background-color 0.3s ease;
}

.pain-card:last-child {
  border-bottom: 1px solid var(--color-border);
}

.pain-card:hover {
  border-color: rgba(201, 169, 110, 0.35);
  background-color: #1a1a1a;
}

.pain-card:hover + .pain-card {
  border-top-color: rgba(201, 169, 110, 0.35);
}

.pain-card__icon {
  color: var(--color-gold);
  flex-shrink: 0;
  margin-top: 0.15rem;
  opacity: 0.85;
  transition: opacity 0.3s ease;
}

.pain-card:hover .pain-card__icon {
  opacity: 1;
}

.pain-card__text {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}

.pain-card__title {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 400;
  color: var(--color-text);
  letter-spacing: 0.01em;
}

.pain-card__desc {
  font-size: 0.875rem;
  font-weight: 300;
  line-height: 1.6;
  color: var(--color-muted);
}

/* =============================================
   Bottom conclusion
   ============================================= */
.about__bottom {
  margin-top: clamp(2.5rem, 5vw, 4rem);
}

.about__conclusion {
  font-size: clamp(1rem, 1.5vw, 1.125rem);
  font-weight: 300;
  line-height: 1.7;
  color: var(--color-muted);
  max-width: 60ch;
  text-align: center;
  margin-inline: auto;
}

.about__conclusion strong {
  color: var(--color-primary);
  font-weight: 400;
}
</style>
