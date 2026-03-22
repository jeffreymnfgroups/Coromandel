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

const faqs = [
  {
    question: 'Do I need any technical knowledge to use this?',
    answer: "No. We handle everything. You don't need to understand SEO, websites, or Google tools. We set it all up and explain what to do next in plain language.",
  },
  {
    question: 'How long does the setup take?',
    answer: 'Most businesses are fully set up within 5-7 working days.',
  },
  {
    question: 'Will this guarantee me a top ranking on Google?',
    answer: "We don't make ranking guarantees — and anyone who does is misleading you. What we do is build a strong, consistent foundation of trust signals, correct information, reviews, and local relevance that supports better visibility over time.",
  },
  {
    question: 'My business is small. Is this still worth it?',
    answer: "Especially for small businesses. The businesses that look professional and trustworthy online are the ones that win customers from competitors who haven't bothered. This is exactly the edge that small businesses need.",
  },
  {
    question: 'What if I already have a Google profile?',
    answer: "Most existing profiles are incomplete or under-optimized. We audit what you have and improve it properly — including things most people miss like category depth, keyword placement, and photo strategy.",
  },
  {
    question: 'Is the price a one-time cost?',
    answer: "Yes. The Complete Business Pack is a one-time setup cost. We'll be transparent about any optional ongoing services if relevant to your goals.",
  },
]

const openIndex = ref(-1)

function toggle(index) {
  openIndex.value = openIndex.value === index ? -1 : index
}
</script>

<template>
  <section class="faq section-hidden" :class="{ 'section-visible': visible }" id="faq" ref="sectionRef">
    <div class="faq__inner container">

      <div class="faq__header">
        <p class="faq__label">FAQ</p>
        <h2 class="faq__heading">
          Frequently Asked<br><em>Questions</em>
        </h2>
      </div>

      <div class="faq__list">
        <div
          v-for="(faq, i) in faqs"
          :key="i"
          class="faq-item"
          :class="{ 'faq-item--open': openIndex === i }"
        >
          <button
            class="faq-item__question"
            @click="toggle(i)"
            :aria-expanded="openIndex === i"
          >
            <span>{{ faq.question }}</span>
            <svg class="faq-item__chevron" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="6 9 12 15 18 9"/></svg>
          </button>
          <div class="faq-item__answer-wrap">
            <p class="faq-item__answer">{{ faq.answer }}</p>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.faq {
  background-color: var(--color-surface);
  padding-block: var(--section-padding);
  position: relative;
}

.faq::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-border), transparent);
}

.faq__inner {
  max-width: 52rem;
  margin-inline: auto;
}

.faq__header {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  margin-bottom: clamp(3rem, 6vw, 4.5rem);
  text-align: center;
  align-items: center;
}

.faq__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.faq__label::before,
.faq__label::after {
  content: '';
  display: inline-block;
  width: 1.5rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.faq__heading {
  font-family: var(--font-display);
  font-size: clamp(2.25rem, 5vw, 3.75rem);
  font-weight: 400;
  line-height: 1.1;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.faq__heading em {
  font-style: italic;
  color: var(--color-primary);
}

/* ---- Accordion ---- */
.faq__list {
  display: flex;
  flex-direction: column;
  border: 1px solid var(--color-border);
}

.faq-item {
  border-bottom: 1px solid var(--color-border);
}

.faq-item:last-child {
  border-bottom: none;
}

.faq-item__question {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1.5rem;
  width: 100%;
  padding: 1.5rem clamp(1.25rem, 3vw, 2rem);
  text-align: left;
  font-family: var(--font-display);
  font-size: clamp(1.0625rem, 2vw, 1.25rem);
  font-weight: 400;
  color: var(--color-text);
  cursor: pointer;
  background: none;
  border: none;
  transition: color 0.2s ease;
}

.faq-item__question:hover {
  color: var(--color-primary);
}

.faq-item__chevron {
  flex-shrink: 0;
  color: var(--color-gold);
  transition: transform 0.3s ease;
}

.faq-item--open .faq-item__chevron {
  transform: rotate(180deg);
}

.faq-item__answer-wrap {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.faq-item--open .faq-item__answer-wrap {
  max-height: 20rem;
}

.faq-item__answer {
  padding: 0 clamp(1.25rem, 3vw, 2rem) 1.5rem;
  font-size: 0.9rem;
  font-weight: 300;
  line-height: 1.8;
  color: var(--color-muted);
}
</style>
