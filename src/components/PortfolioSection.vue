<script setup>
import { ref, onMounted } from 'vue'
import img4 from '@/assets/1 (4).webp'
import img5 from '@/assets/1 (5).webp'
import img6 from '@/assets/1 (6).webp'
import img7 from '@/assets/1 (7).webp'
import img8 from '@/assets/1 (8).webp'
import img9 from '@/assets/1 (9).webp'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.1 }
  )
  observer.observe(sectionRef.value)
})

const deepDives = [
  {
    title: 'Get Found Faster on Google and Maps',
    body: `When someone nearby searches "salon near me" or "best clinic in Pondichery," your Google Business Profile is the first thing they see. If that profile looks incomplete, outdated, or thin, they scroll past. We optimize everything that matters — business category, keyword-rich descriptions, photo uploads with proper tagging, regular post strategy, Q&A optimization, and complete information that leaves no questions unanswered.`,
    result: 'Your business becomes easier to discover, easier to trust, and more likely to receive calls.',
    image: img4,
    tag: 'Google Business',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/>ircle cx="12" cy="10" r="3"/></svg>`,
  },
  {
    title: 'We Find the Keywords Your Customers Already Use',
    body: `Local customers don't just search "salon" or "doctor." They search "ladies salon in Marthandam," "best dental clinic near Pondichery bus stand," "cake shop open Sunday Thuckalay." We identify service + city combinations, high-intent buyer phrases, neighborhood-specific terms, gaps competitors haven't captured, and search volume opportunities for your category.`,
    result: 'Your profile and website speak the exact language your customers use.',
    image: img5,
    tag: 'Keyword Strategy',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">ircle cx="11" cy="11" r="8"/>e x1="21" y1="21" x2="16.65" y2="16.65"/></svg>`,
  },
  {
    title: 'Make Review Collection Easy Instead of Awkward',
    body: `Most happy customers intend to leave a review but forget. Asking feels awkward, sending reminders feels pushy. We solve that with a simple QR code review flow — the customer scans a code at your counter, bill, or table stand and lands directly on your Google review page. No searching, no confusion, no extra steps. Just one tap and they're writing their review.`,
    result: 'More consistent reviews, less awkward follow-up, and a growing reputation built naturally.',
    image: img6,
    tag: 'Review QR Flow',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2" ry="2"/><rect x="7" y="7" width="3" height="3"/><rect x="14" y="7" width="3" height="3"/><rect x="7" y="14" width="3" height="3"/><rect x="14" y="14" width="3" height="3"/></svg>`,
  },
  {
    title: 'Turn Every Review Into a Trust Signal',
    body: `Collecting reviews is only half the work. A good reply tells every future visitor something important: this business pays attention. They care. They're real. We help you respond in a way that shows warmth, naturally includes your service and location context, keeps your profile active and engaged, and makes new visitors feel confident before they've even called.`,
    result: 'Your profile looks alive, responsive, and trustworthy — not like an abandoned listing.',
    image: img7,
    tag: 'Reputation Management',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>`,
  },
  {
    title: 'Let Customers Reach You Instantly',
    body: `A location QR code removes the "I'm not sure where you are" barrier entirely. Scan it and Google Maps opens with directions. Use it on shop boards, bill receipts, packaging, table stands, brochures, WhatsApp messages, and social media. Every scan is a potential walk-in that almost didn't happen.`,
    result: 'Getting to your business becomes effortless. No manual searching, no wrong turns.',
    image: img8,
    tag: 'Location QR',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="3 11 22 2 13 21 11 13 3 11"/></svg>`,
  },
  {
    title: 'A Website That Works Like a 24/7 Salesperson',
    body: `At 11 PM when a customer is searching for a salon to book tomorrow, your website can explain your services, show your work, and give them a way to WhatsApp you. It educates, builds trust, and converts — what you do, why you're different, who you serve, proof of your work, and easy contact with click-to-call and WhatsApp buttons.`,
    result: 'More enquiries outside business hours and a stronger first impression for every visitor.',
    image: img9,
    tag: 'Local Website',
    icon: `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="3" width="20" height="14" rx="2" ry="2"/>e x1="8" y1="21" x2="16" y2="21"/>e x1="12" y1="17" x2="12" y2="21"/></svg>`,
  },
]
</script>

<template>
  <section
    class="deepdives section-hidden"
    :class="{ 'section-visible': visible }"
    id="deep-dives"
    ref="sectionRef"
  >
    <div class="deepdives__inner container">

      <!-- Header -->
      <div class="deepdives__header">
        <p class="deepdives__label">Service Deep-Dives</p>
        <h2 class="deepdives__heading">
          How each piece<br><em>works for you</em>
        </h2>
      </div>

      <!-- Grid -->
      <div class="deepdives__grid">
        <article
          v-for="item in deepDives"
          :key="item.title"
          class="dive-card"
        >
          <!-- Image Banner -->
          <div class="dive-card__image-wrap">
            <img
              :src="item.image"
              :alt="item.title"
              class="dive-card__image"
              loading="lazy"
            />
            <div class="dive-card__image-overlay"></div>
            <span class="dive-card__tag">{{ item.tag }}</span>
          </div>

          <!-- Content -->
          <div class="dive-card__content">
            <div class="dive-card__header">
              <div class="dive-card__icon" v-html="item.icon" aria-hidden="true"></div>
              <h3 class="dive-card__title">{{ item.title }}</h3>
            </div>
            <p class="dive-card__body">{{ item.body }}</p>
            <div class="dive-card__result">
              <svg class="dive-card__result-icon" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                <polyline points="20 6 9 17 4 12"/>
              </svg>
              <span>{{ item.result }}</span>
            </div>
          </div>
        </article>
      </div>

    </div>
  </section>
</template>

<style scoped>
/* =============================================
   Section
   ============================================= */
.deepdives {
  background-color: var(--color-surface);
  padding-block: var(--section-padding);
  position: relative;
}

.deepdives::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-border), transparent);
}

/* =============================================
   Header
   ============================================= */
.deepdives__header {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  margin-bottom: clamp(3rem, 6vw, 4.5rem);
}

.deepdives__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.deepdives__label::before {
  content: '';
  display: inline-block;
  width: 2rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.deepdives__heading {
  font-family: var(--font-display);
  font-size: clamp(2.25rem, 5vw, 3.75rem);
  font-weight: 400;
  line-height: 1.1;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.deepdives__heading em {
  font-style: italic;
  color: var(--color-primary);
}

/* =============================================
   Grid
   ============================================= */
.deepdives__grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.75rem;
}

@media (min-width: 768px) {
  .deepdives__grid {
    grid-template-columns: 1fr 1fr;
  }
}

/* =============================================
   Card
   ============================================= */
.dive-card {
  display: flex;
  flex-direction: column;
  border: 1px solid var(--color-border);
  background-color: var(--color-bg);
  overflow: hidden;
  transition: border-color 0.35s ease, transform 0.35s ease, box-shadow 0.35s ease;
}

.dive-card:hover {
  border-color: rgba(201, 169, 110, 0.4);
  transform: translateY(-4px);
  box-shadow: 0 16px 40px rgba(0, 0, 0, 0.18);
}

/* =============================================
   Image Block
   ============================================= */
.dive-card__image-wrap {
  position: relative;
  width: 100%;
  height: 200px;
  overflow: hidden;
  flex-shrink: 0;
}

.dive-card__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.6s ease;
  filter: brightness(0.72) saturate(0.85);
}

.dive-card:hover .dive-card__image {
  transform: scale(1.05);
  filter: brightness(0.6) saturate(0.9);
}

/* Dark gradient fade into card background */
.dive-card__image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    transparent 30%,
    var(--color-bg) 100%
  );
  pointer-events: none;
}

/* Pill tag on the image */
.dive-card__tag {
  position: absolute;
  top: 1rem;
  left: 1rem;
  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--color-gold);
  background: rgba(0, 0, 0, 0.55);
  border: 1px solid rgba(201, 169, 110, 0.35);
  padding: 0.3rem 0.75rem;
  backdrop-filter: blur(6px);
  -webkit-backdrop-filter: blur(6px);
}

/* =============================================
   Card Content
   ============================================= */
.dive-card__content {
  display: flex;
  flex-direction: column;
  gap: 1.1rem;
  padding: clamp(1.5rem, 3vw, 2rem);
  flex: 1;
}

.dive-card__header {
  display: flex;
  align-items: flex-start;
  gap: 0.875rem;
}

.dive-card__icon {
  color: var(--color-gold);
  flex-shrink: 0;
  opacity: 0.85;
  margin-top: 0.15rem;
  transition: opacity 0.3s ease;
}

.dive-card:hover .dive-card__icon {
  opacity: 1;
}

.dive-card__title {
  font-family: var(--font-display);
  font-size: 1.2rem;
  font-weight: 400;
  color: var(--color-text);
  line-height: 1.3;
  transition: color 0.3s ease;
}

.dive-card:hover .dive-card__title {
  color: var(--color-primary);
}

.dive-card__body {
  font-size: 0.875rem;
  font-weight: 300;
  line-height: 1.8;
  color: var(--color-muted);
  flex: 1;
}

.dive-card__result {
  display: flex;
  align-items: flex-start;
  gap: 0.65rem;
  padding-top: 1rem;
  border-top: 1px solid var(--color-border);
  font-size: 0.82rem;
  font-weight: 400;
  color: var(--color-primary);
  line-height: 1.5;
}

.dive-card__result-icon {
  flex-shrink: 0;
  color: var(--color-gold);
  margin-top: 0.15rem;
}
</style>
