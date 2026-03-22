<script setup>
import { ref, onMounted } from 'vue'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => { setTimeout(() => { visible.value = true }, 100) })
</script>

<template>
  <section class="hero section-hidden" :class="{ 'section-visible': visible }" id="hero" ref="sectionRef">
    <div class="hero__inner container">

      <!-- Left: copy -->
      <div class="hero__content">
        <p class="hero__label">Local Growth Partner</p>

        <h1 class="hero__headline">
          Turn Your Local Business Into a<br>
          <em>Trusted Brand on Google</em>
        </h1>

        <p class="hero__sub">
          We help local businesses get discovered on Google, build genuine trust
          through reviews, and convert more visitors into calls, WhatsApp enquiries,
          and walk-ins — with one complete, affordable system.
        </p>

        <div class="hero__actions">
          <a href="#contact" class="hero__btn hero__btn--filled">
            <svg class="hero__btn-icon" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
            Book Free Demo
          </a>
          <a href="https://wa.me/919500511297" target="_blank" rel="noopener" class="hero__btn hero__btn--outline">
            <svg class="hero__btn-icon" width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413z"/></svg>
            WhatsApp Us Now
          </a>
        </div>

        <p class="hero__note">
          Built for shops, clinics, restaurants, salons, and service businesses
          that want more enquiries — not more confusion.
        </p>
      </div>

      <!-- Right: abstract visual -->
      <div class="hero__visual" aria-hidden="true">
        <div class="orb"></div>
        <div class="orb__ring orb__ring--1"></div>
        <div class="orb__ring orb__ring--2"></div>
        <div class="orb__ring orb__ring--3"></div>
        <div class="orb__line orb__line--h"></div>
        <div class="orb__line orb__line--v"></div>
        <div class="orb__dot orb__dot--1"></div>
        <div class="orb__dot orb__dot--2"></div>
        <div class="orb__dot orb__dot--3"></div>
      </div>

    </div>

    <!-- Bottom gradient fade -->
    <div class="hero__fade" aria-hidden="true"></div>
  </section>
</template>

<style scoped>
/* =============================================
   Section
   ============================================= */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
  background-color: var(--color-bg);
}

/* Subtle radial background glow behind everything */
.hero::before {
  content: '';
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse 60% 50% at 70% 50%, rgba(201, 169, 110, 0.06) 0%, transparent 70%),
    radial-gradient(ellipse 40% 60% at 20% 30%, rgba(232, 224, 208, 0.03) 0%, transparent 60%);
  pointer-events: none;
}

.hero__fade {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 8rem;
  background: linear-gradient(to bottom, transparent, var(--color-bg));
  pointer-events: none;
}

/* =============================================
   Layout
   ============================================= */
.hero__inner {
  display: grid;
  grid-template-columns: 1fr;
  gap: clamp(2rem, 5vw, 4rem);
  align-items: center;
  padding-top: clamp(5rem, 10vw, 6rem);
  padding-bottom: clamp(2.5rem, 5vw, 4rem);
  width: 100%;
}

/* =============================================
   Content (left)
   ============================================= */
.hero__content {
  display: flex;
  flex-direction: column;
  gap: 1.75rem;
  animation: fadeUp 0.9s cubic-bezier(0.4, 0, 0.2, 1) both;
}

.hero__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.hero__label::before {
  content: '';
  display: inline-block;
  width: 2rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.hero__headline {
  font-family: var(--font-display);
  font-size: clamp(2.75rem, 6vw, 5rem);
  font-weight: 400;
  line-height: 1.08;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.hero__headline em {
  font-style: italic;
  color: var(--color-primary);
}

.hero__sub {
  font-size: clamp(0.9375rem, 1.5vw, 1.0625rem);
  font-weight: 300;
  line-height: 1.7;
  color: var(--color-muted);
  max-width: 48ch;
}

.hero__actions {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  padding-top: 0.5rem;
}

/* ---- Buttons ---- */
.hero__btn {
  font-size: 0.8rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  padding: 0.85rem 2rem;
  transition: background-color 0.25s ease, color 0.25s ease, border-color 0.25s ease;
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
}

.hero__btn-icon {
  flex-shrink: 0;
}

.hero__btn--filled {
  background-color: var(--color-gold);
  color: var(--color-bg);
  border: 1px solid var(--color-gold);
}

.hero__btn--filled:hover {
  background-color: var(--color-primary);
  border-color: var(--color-primary);
}

.hero__btn--outline {
  background-color: transparent;
  color: var(--color-primary);
  border: 1px solid var(--color-border);
}

.hero__btn--outline:hover {
  border-color: var(--color-primary);
  color: var(--color-text);
}

.hero__note {
  font-size: 0.8125rem;
  font-weight: 300;
  color: #4a4a4a;
  line-height: 1.6;
  font-style: italic;
  max-width: 48ch;
}

/* =============================================
   Visual (right) — CSS orb
   ============================================= */
.hero__visual {
  position: relative;
  width: 100%;
  max-width: 26rem;
  aspect-ratio: 1;
  margin-inline: auto;
  animation: fadeIn 1.2s cubic-bezier(0.4, 0, 0.2, 1) 0.3s both;
}

/* Core glowing orb */
.orb {
  position: absolute;
  inset: 18%;
  border-radius: 50%;
  background: radial-gradient(
    circle at 38% 38%,
    rgba(232, 224, 208, 0.18) 0%,
    rgba(201, 169, 110, 0.22) 35%,
    rgba(201, 169, 110, 0.06) 65%,
    transparent 100%
  );
  box-shadow:
    0 0 60px 10px rgba(201, 169, 110, 0.12),
    0 0 120px 30px rgba(201, 169, 110, 0.06),
    inset 0 0 40px rgba(232, 224, 208, 0.05);
  animation: pulse 6s ease-in-out infinite;
}

/* Concentric rings */
.orb__ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid rgba(201, 169, 110, 0.18);
}

.orb__ring--1 {
  inset: 10%;
  animation: spin 28s linear infinite;
  border-style: dashed;
  border-color: rgba(201, 169, 110, 0.1);
}

.orb__ring--2 {
  inset: 3%;
  border-color: rgba(201, 169, 110, 0.08);
  animation: spin 40s linear infinite reverse;
}

.orb__ring--3 {
  inset: -5%;
  border-color: rgba(232, 224, 208, 0.05);
  border-style: dashed;
  animation: spin 55s linear infinite;
}

/* Cross-hair lines through center */
.orb__line {
  position: absolute;
  background: linear-gradient(to right, transparent, rgba(201, 169, 110, 0.15), transparent);
  top: 50%;
  left: 0;
  right: 0;
  height: 1px;
  transform: translateY(-50%);
}

.orb__line--v {
  background: linear-gradient(to bottom, transparent, rgba(201, 169, 110, 0.15), transparent);
  top: 0;
  bottom: 0;
  left: 50%;
  right: auto;
  width: 1px;
  height: auto;
  transform: translateX(-50%);
}

/* Orbiting dots */
.orb__dot {
  position: absolute;
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background-color: var(--color-gold);
  box-shadow: 0 0 8px 2px rgba(201, 169, 110, 0.5);
}

.orb__dot--1 {
  top: 12%;
  left: 50%;
  transform: translateX(-50%);
  animation: orbitV 8s ease-in-out infinite;
  opacity: 0.8;
}

.orb__dot--2 {
  top: 50%;
  right: 10%;
  transform: translateY(-50%);
  animation: orbitH 11s ease-in-out infinite reverse;
  opacity: 0.6;
  width: 3px;
  height: 3px;
}

.orb__dot--3 {
  bottom: 20%;
  left: 20%;
  animation: orbitDiag 14s ease-in-out infinite;
  opacity: 0.5;
  width: 4px;
  height: 4px;
}

/* =============================================
   Animations
   ============================================= */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(28px); }
  to   { opacity: 1; transform: translateY(0); }
}

@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.94); }
  to   { opacity: 1; transform: scale(1); }
}

@keyframes pulse {
  0%, 100% { transform: scale(1);    opacity: 1; }
  50%       { transform: scale(1.04); opacity: 0.85; }
}

@keyframes spin {
  to { transform: rotate(360deg); }
}

@keyframes orbitV {
  0%, 100% { transform: translateX(-50%) translateY(0); }
  50%       { transform: translateX(-50%) translateY(calc(76% - 5px)); }
}

@keyframes orbitH {
  0%, 100% { transform: translateY(-50%) translateX(0); }
  50%       { transform: translateY(-50%) translateX(calc(-80% + 5px)); }
}

@keyframes orbitDiag {
  0%, 100% { transform: translate(0, 0); }
  50%       { transform: translate(calc(60% - 5px), calc(-60% + 5px)); }
}

/* =============================================
   Responsive
   ============================================= */
@media (max-width: 480px) {
  .hero__visual {
    max-width: 16rem;
  }
}

@media (min-width: 768px) {
  .hero__inner {
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
    padding-top: 8rem;
    padding-bottom: 6rem;
  }

  .hero__visual {
    max-width: none;
    margin-inline: 0;
  }
}

@media (min-width: 1024px) {
  .hero__inner {
    grid-template-columns: 55% 45%;
  }
}
</style>
