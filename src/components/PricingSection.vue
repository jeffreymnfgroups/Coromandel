<script setup>
import { ref, onMounted } from 'vue'
import img18 from '@/assets/1 (18).webp'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.1 }
  )
  observer.observe(sectionRef.value)
})

const included = [
  'Google Business Profile optimization — complete setup, categories, services, photos, keywords, posts, Q&A',
  'Local keyword research — real search terms your customers use',
  'Review QR code system — simple, scannable, friction-free',
  'Location QR code — directions in one scan',
  'SEO-friendly review reply guidance — so every response builds trust',
  'Professional local business website — clear, fast, mobile-ready',
  'Lead capture form + WhatsApp CTA — enquiries even after hours',
  'Domain + hosting setup support — we guide you through it',
]
</script>

<template>
  <section class="pricing section-hidden" :class="{ 'section-visible': visible }" id="pricing" ref="sectionRef">
    <div class="pricing__inner container">

      <div class="pricing__header">
        <p class="pricing__label">The Offer</p>
        <h2 class="pricing__heading">
          Complete Business Pack —<br><em>Everything You Need</em>
        </h2>
        <p class="pricing__sub">
          A full local growth setup for businesses that want better visibility,
          stronger reputation, and more enquiries — without spending a huge amount.
        </p>
      </div>

      <div class="pricing__card">
        <div class="pricing__card-bg">
          <img :src="img18" alt="Premium pricing" class="pricing__bg-img" />
          <div class="pricing__bg-overlay"></div>
        </div>
        
        <!-- Checklist -->
        <div class="pricing__list">
          <h3 class="pricing__list-title">What's Included</h3>
          <ul class="pricing__items">
            <li v-for="item in included" :key="item" class="pricing__item">
              <svg class="pricing__check" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>
              <span>{{ item }}</span>
            </li>
          </ul>
        </div>

        <!-- Price + CTAs -->
        <div class="pricing__cta-area">
          <div class="pricing__price">
            <span class="pricing__original">₹12,000</span>
            <span class="pricing__current">₹5,999</span>
            <span class="pricing__badge">Limited-Time Offer</span>
          </div>

          <p class="pricing__value-msg">
            For local businesses that want a smarter online presence,
            stronger trust, and better enquiry flow — starting this week.
          </p>

          <div class="pricing__actions">
            <a href="#contact" class="pricing__btn pricing__btn--primary">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
              Get My Growth Pack
            </a>
            <a href="https://wa.me/919500511297" target="_blank" rel="noopener" class="pricing__btn pricing__btn--outline">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413z"/></svg>
              Talk to Us on WhatsApp
            </a>
            <a href="#contact" class="pricing__btn pricing__btn--outline">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
              Book Free Demo
            </a>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.pricing {
  background-color: var(--color-bg);
  padding-block: var(--section-padding);
  position: relative;
}

.pricing::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-border), transparent);
}

.pricing__header {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  margin-bottom: clamp(3rem, 6vw, 5rem);
  text-align: center;
  align-items: center;
}

.pricing__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.pricing__label::before,
.pricing__label::after {
  content: '';
  display: inline-block;
  width: 1.5rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.pricing__heading {
  font-family: var(--font-display);
  font-size: clamp(2.25rem, 5vw, 3.75rem);
  font-weight: 400;
  line-height: 1.1;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.pricing__heading em {
  font-style: italic;
  color: var(--color-primary);
}

.pricing__sub {
  font-size: 0.9375rem;
  font-weight: 300;
  line-height: 1.7;
  color: var(--color-muted);
  max-width: 52ch;
}

/* ---- Card ---- */
.pricing__card {
  border: 1px solid rgba(201, 169, 110, 0.25);
  background: #111;
  padding: clamp(2rem, 5vw, 3.5rem);
  display: grid;
  grid-template-columns: 1fr;
  gap: clamp(2.5rem, 5vw, 4rem);
  position: relative;
  overflow: hidden;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
}

.pricing__card-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.pricing__bg-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: grayscale(100%) brightness(0.6);
  opacity: 0.4;
  transition: transform 0.8s ease, opacity 0.8s ease;
}

.pricing__bg-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(13,13,13,0.95) 0%, rgba(13,13,13,0.7) 100%);
}

.pricing__card:hover .pricing__bg-img {
  transform: scale(1.05);
  opacity: 0.6;
}

.pricing__list,
.pricing__cta-area {
  position: relative;
  z-index: 1;
}

@media (min-width: 900px) {
  .pricing__card {
    grid-template-columns: 1.3fr 1fr;
  }
}

.pricing__card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4rem;
  height: 1px;
  background-color: var(--color-gold);
  opacity: 0.7;
}

.pricing__card::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 1px;
  height: 4rem;
  background-color: var(--color-gold);
  opacity: 0.7;
}

/* ---- Checklist ---- */
.pricing__list-title {
  font-family: var(--font-display);
  font-size: 1.375rem;
  font-weight: 400;
  color: var(--color-text);
  margin-bottom: 1.5rem;
}

.pricing__items {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.pricing__item {
  display: flex;
  align-items: flex-start;
  gap: 0.85rem;
  font-size: 0.9rem;
  font-weight: 300;
  line-height: 1.6;
  color: var(--color-muted);
}

.pricing__check {
  flex-shrink: 0;
  color: var(--color-gold);
  margin-top: 0.2rem;
}

/* ---- Price + CTA area ---- */
.pricing__cta-area {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  justify-content: center;
}

.pricing__price {
  display: flex;
  align-items: baseline;
  gap: 1rem;
  flex-wrap: wrap;
}

.pricing__original {
  font-family: var(--font-display);
  font-size: 1.5rem;
  font-weight: 400;
  color: var(--color-muted);
  text-decoration: line-through;
  opacity: 0.6;
}

.pricing__current {
  font-family: var(--font-display);
  font-size: clamp(3rem, 6vw, 4rem);
  font-weight: 400;
  color: var(--color-text);
  line-height: 1;
  letter-spacing: -0.02em;
}

.pricing__badge {
  font-size: 0.6875rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--color-gold);
  background-color: rgba(201, 169, 110, 0.1);
  border: 1px solid rgba(201, 169, 110, 0.2);
  padding: 0.3rem 0.75rem;
  align-self: center;
}

.pricing__value-msg {
  font-size: 0.9rem;
  font-weight: 300;
  line-height: 1.7;
  color: var(--color-muted);
}

.pricing__actions {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.pricing__btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.65rem;
  font-size: 0.8rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  padding: 0.9rem 2rem;
  text-decoration: none;
  transition: background-color 0.25s ease, border-color 0.25s ease, color 0.25s ease;
  white-space: nowrap;
}

.pricing__btn--primary {
  background-color: var(--color-gold);
  color: var(--color-bg);
  border: 1px solid var(--color-gold);
}

.pricing__btn--primary:hover {
  background-color: var(--color-primary);
  border-color: var(--color-primary);
}

.pricing__btn--outline {
  background-color: transparent;
  color: var(--color-primary);
  border: 1px solid var(--color-border);
}

.pricing__btn--outline:hover {
  border-color: var(--color-primary);
  color: var(--color-text);
}
</style>
