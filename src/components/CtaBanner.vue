<script setup>
import { ref, onMounted } from 'vue'

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
</script>

<template>
  <section
    class="cta"
    :class="{ 'is-visible': visible }"
    ref="sectionRef"
  >
    <div class="cta__inner container">
      <div class="cta__box">

        <!-- Corner accents (all 4) -->
        <span class="corner corner--tl" aria-hidden="true" />
        <span class="corner corner--tr" aria-hidden="true" />
        <span class="corner corner--bl" aria-hidden="true" />
        <span class="corner corner--br" aria-hidden="true" />

        <!-- Ambient glow blob -->
        <div class="cta__glow" aria-hidden="true" />

        <div class="cta__layout">

          <!-- ── Left: Content ── -->
          <div class="cta__content">
            <span class="cta__badge">
              <svg width="10" height="10" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
                <circle cx="12" cy="12" r="12"/>
              </svg>
              Limited Time Offer
            </span>

            <h2 class="cta__heading">
              Your Business<br>Deserves to Be <em>Found</em>
            </h2>

            <p class="cta__sub">
              Every day without a complete online presence is a day you're leaving
              enquiries on the table. The customer who searched for you last Tuesday
              and found a competitor instead? They didn't know you were better —
              they just knew the other business looked more prepared.
            </p>

            <p class="cta__sub cta__sub--accent">Let's fix that.</p>
          </div>

          <!-- ── Right: Offer card + Actions ── -->
          <div class="cta__aside">
            <div class="cta__offer-card">
              <p class="cta__offer-label">Complete Business Pack</p>
              <div class="cta__price-row">
                <span class="cta__price">₹5,999</span>
                <span class="cta__price-tag">one-time</span>
              </div>
              <p class="cta__offer-desc">
                Start building a local online presence that works for you every single day.
              </p>
              <ul class="cta__checklist" aria-label="What's included">
                <li>Google Business Profile setup</li>
                <li>Local SEO foundations</li>
                <li>Business listings across directories</li>
                <li>Ongoing support &amp; guidance</li>
              </ul>
            </div>

            <div class="cta__actions">
              <a href="#contact" class="cta__btn cta__btn--filled">
                <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                  stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
                  <rect x="3" y="4" width="18" height="18" rx="2" ry="2"/>
                  <line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/>
                  <line x1="3" y1="10" x2="21" y2="10"/>
                </svg>
                Book Free Demo
              </a>

              <a href="https://wa.me/919876543210" target="_blank" rel="noopener noreferrer"
                class="cta__btn cta__btn--whatsapp">
                <svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
                  <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413z"/>
                </svg>
                WhatsApp Us
              </a>

              <a href="#contact" class="cta__btn cta__btn--ghost">
                <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor"
                  stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
                  <line x1="22" y1="2" x2="11" y2="13"/>
                  <polygon points="22 2 15 22 11 13 2 9 22 2"/>
                </svg>
                Start My Local Growth
              </a>
            </div>
          </div>

        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* ── Reveal animation ─────────────────────────────────── */
.cta {
  opacity: 0;
  transform: translateY(32px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.cta.is-visible {
  opacity: 1;
  transform: translateY(0);
}

/* Stagger child elements */
.cta.is-visible .cta__badge   { animation: fadeUp 0.5s ease 0.05s both; }
.cta.is-visible .cta__heading { animation: fadeUp 0.55s ease 0.15s both; }
.cta.is-visible .cta__sub     { animation: fadeUp 0.55s ease 0.25s both; }
.cta.is-visible .cta__aside   { animation: fadeUp 0.6s ease 0.35s both; }

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* ── Section shell ────────────────────────────────────── */
.cta {
  background-color: var(--color-bg);
  padding-block: var(--section-padding);
  position: relative;
}

.cta::before {
  content: '';
  position: absolute;
  inset: 0 0 auto 0;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-border), transparent);
}

/* ── Main box ─────────────────────────────────────────── */
.cta__box {
  position: relative;
  overflow: hidden;
  border: 1px solid rgba(201, 169, 110, 0.2);
  background: linear-gradient(135deg, #111 0%, #0d0d0d 60%, #0f0f0f 100%);
  padding: clamp(2.5rem, 6vw, 4.5rem) clamp(1.75rem, 5vw, 4rem);
}

/* ── All-corner gold accents ──────────────────────────── */
.corner {
  position: absolute;
  width: 3.5rem;
  height: 3.5rem;
  pointer-events: none;
}
.corner::before,
.corner::after {
  content: '';
  position: absolute;
  background-color: var(--color-gold, #c9a96e);
  opacity: 0.65;
}
.corner::before { width: 100%; height: 1px; }
.corner::after  { width: 1px; height: 100%; }

.corner--tl { top: 0; left: 0; }
.corner--tr { top: 0; right: 0; transform: scaleX(-1); }
.corner--bl { bottom: 0; left: 0; transform: scaleY(-1); }
.corner--br { bottom: 0; right: 0; transform: scale(-1); }

/* ── Ambient glow ─────────────────────────────────────── */
.cta__glow {
  position: absolute;
  top: -40%;
  right: -10%;
  width: 55%;
  aspect-ratio: 1;
  background: radial-gradient(circle, rgba(201, 169, 110, 0.07) 0%, transparent 70%);
  pointer-events: none;
  border-radius: 50%;
}

/* ── Two-column layout ────────────────────────────────── */
.cta__layout {
  position: relative;
  display: grid;
  grid-template-columns: 1fr;
  gap: 2.5rem;
}

@media (min-width: 900px) {
  .cta__layout {
    grid-template-columns: 1fr 380px;
    gap: 3.5rem;
    align-items: start;
  }
}

/* ── Left content ─────────────────────────────────────── */
.cta__content {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.cta__badge {
  display: inline-flex;
  align-items: center;
  gap: 0.45rem;
  font-size: 0.6875rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--color-gold, #c9a96e);
  border: 1px solid rgba(201, 169, 110, 0.3);
  padding: 0.3rem 0.85rem;
  width: fit-content;
}

.cta__badge svg {
  width: 6px;
  height: 6px;
  color: var(--color-gold, #c9a96e);
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50%       { opacity: 0.35; }
}

.cta__heading {
  font-family: var(--font-display);
  font-size: clamp(2rem, 4.5vw, 3.5rem);
  font-weight: 400;
  line-height: 1.1;
  color: var(--color-text);
  letter-spacing: -0.01em;
  margin: 0;
}

.cta__heading em {
  font-style: italic;
  color: var(--color-primary, #c9a96e);
}

.cta__sub {
  font-size: 0.9375rem;
  font-weight: 300;
  line-height: 1.75;
  color: var(--color-muted);
  max-width: 54ch;
  margin: 0;
}

.cta__sub--accent {
  color: var(--color-text);
  font-weight: 400;
}

/* ── Right aside ──────────────────────────────────────── */
.cta__aside {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

/* ── Offer card ───────────────────────────────────────── */
.cta__offer-card {
  background: rgba(201, 169, 110, 0.05);
  border: 1px solid rgba(201, 169, 110, 0.2);
  padding: 1.75rem;
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
}

.cta__offer-label {
  font-size: 0.6875rem;
  font-weight: 500;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--color-muted);
  margin: 0;
}

.cta__price-row {
  display: flex;
  align-items: baseline;
  gap: 0.6rem;
}

.cta__price {
  font-family: var(--font-display);
  font-size: clamp(2rem, 5vw, 2.75rem);
  font-weight: 400;
  color: var(--color-primary, #c9a96e);
  line-height: 1;
}

.cta__price-tag {
  font-size: 0.75rem;
  color: var(--color-muted);
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.cta__offer-desc {
  font-size: 0.875rem;
  font-weight: 300;
  line-height: 1.65;
  color: var(--color-muted);
  margin: 0;
}

/* ── Checklist ────────────────────────────────────────── */
.cta__checklist {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  border-top: 1px solid rgba(201, 169, 110, 0.12);
  padding-top: 0.85rem;
}

.cta__checklist li {
  font-size: 0.8125rem;
  font-weight: 300;
  color: var(--color-muted);
  padding-left: 1.1rem;
  position: relative;
}

.cta__checklist li::before {
  content: '✓';
  position: absolute;
  left: 0;
  color: var(--color-gold, #c9a96e);
  font-size: 0.7rem;
  top: 1px;
}

/* ── Action buttons ───────────────────────────────────── */
.cta__actions {
  display: flex;
  flex-direction: column;
  gap: 0.65rem;
}

.cta__btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.6rem;
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.13em;
  text-transform: uppercase;
  padding: 0.9rem 1.5rem;
  text-decoration: none;
  white-space: nowrap;
  transition: background-color 0.22s ease, border-color 0.22s ease,
              color 0.22s ease, transform 0.18s ease;
}

.cta__btn:active {
  transform: scale(0.98);
}

/* Filled – primary CTA */
.cta__btn--filled {
  background-color: var(--color-gold, #c9a96e);
  color: #0d0d0d;
  border: 1px solid var(--color-gold, #c9a96e);
  font-weight: 500;
}
.cta__btn--filled:hover {
  background-color: var(--color-primary, #d4b47a);
  border-color: var(--color-primary, #d4b47a);
}

/* WhatsApp */
.cta__btn--whatsapp {
  background-color: rgba(37, 211, 102, 0.08);
  color: #4ade80;
  border: 1px solid rgba(37, 211, 102, 0.25);
}
.cta__btn--whatsapp:hover {
  background-color: rgba(37, 211, 102, 0.14);
  border-color: rgba(37, 211, 102, 0.5);
}

/* Ghost – tertiary */
.cta__btn--ghost {
  background-color: transparent;
  color: var(--color-muted);
  border: 1px solid rgba(255, 255, 255, 0.08);
}
.cta__btn--ghost:hover {
  border-color: rgba(201, 169, 110, 0.35);
  color: var(--color-text);
}

/* ── Responsive tweaks ────────────────────────────────── */
@media (min-width: 540px) and (max-width: 899px) {
  .cta__actions {
    flex-direction: row;
    flex-wrap: wrap;
  }
  .cta__btn {
    flex: 1 1 auto;
  }
}

@media (max-width: 539px) {
  .cta__offer-card {
    padding: 1.25rem;
  }
}
</style>
