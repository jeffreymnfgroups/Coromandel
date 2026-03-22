<script setup>
import { computed, ref, onMounted } from 'vue'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.15 }
  )
  observer.observe(sectionRef.value)
})

const year = computed(() => new Date().getFullYear())

const serviceLinks = [
  'Google Profile Optimization',
  'Review Growth System',
  'Local Business Website',
  'Keyword Research',
]

const quickLinks = [
  { label: 'Services',     href: '#services' },
  { label: 'How It Works', href: '#how-it-works' },
  { label: 'Pricing',      href: '#pricing' },
  { label: 'FAQ',          href: '#faq' },
  { label: 'Contact',      href: '#contact' },
]

function scrollTo(hash) {
  const el = document.querySelector(hash)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <footer class="footer section-hidden" :class="{ 'section-visible': visible }" ref="sectionRef">
    <!-- Top border accent -->
    <div class="footer__accent" aria-hidden="true"></div>

    <div class="footer__body container">

      <!-- Col 1: Brand -->
      <div class="footer__brand">
        <a href="#hero" class="footer__logo" @click.prevent="scrollTo('#hero')">
          Corom<span class="footer__logo-accent">a</span>ndel
        </a>
        <p class="footer__tagline">Get found. Get trusted. Get chosen.</p>
        <p class="footer__desc">
          We help local businesses build a stronger online presence
          with Google optimization, review systems, and professional websites.
        </p>
      </div>

      <!-- Col 2: Services -->
      <div class="footer__col">
        <p class="footer__col-heading">Services</p>
        <ul class="footer__links">
          <li v-for="service in serviceLinks" :key="service">
            <a href="#services" class="footer__link" @click.prevent="scrollTo('#services')">{{ service }}</a>
          </li>
        </ul>
      </div>

      <!-- Col 3: Quick Links -->
      <div class="footer__col">
        <p class="footer__col-heading">Quick Links</p>
        <ul class="footer__links">
          <li v-for="link in quickLinks" :key="link.label">
            <a :href="link.href" class="footer__link" @click.prevent="scrollTo(link.href)">{{ link.label }}</a>
          </li>
        </ul>
      </div>

      <!-- Col 4: Get In Touch -->
      <div class="footer__col">
        <p class="footer__col-heading">Get In Touch</p>
        <ul class="footer__links footer__contact-links">
          <li>
            <a href="mailto:hello@coromandelbranding.com" class="footer__link">
              hello@coromandelbranding.com
            </a>
          </li>
          <li>
            <a href="tel:+919500511297" class="footer__link">
              +91 95005 11297
            </a>
          </li>
          <li>
            <span class="footer__link footer__link--static">
              Pondichery, Tamil Nadu
            </span>
          </li>
        </ul>

        <!-- WhatsApp -->
        <a href="https://wa.me/919500511297" target="_blank" rel="noopener" class="footer__whatsapp" aria-label="WhatsApp">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413z"/></svg>
          <span>WhatsApp Us</span>
        </a>
      </div>

    </div>

    <!-- Bottom bar -->
    <div class="footer__bottom">
      <div class="footer__bottom-inner container">
        <p class="footer__copy">
          &copy; {{ year }} Corom<span class="footer__logo-accent">a</span>ndel Branding Solutions. All rights reserved.
        </p>
        <p class="footer__mission">We help local businesses get found, get trusted, and get chosen.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
/* =============================================
   Footer
   ============================================= */
.footer {
  background-color: var(--color-bg);
  position: relative;
}

/* Gold gradient top border */
.footer__accent {
  height: 1px;
  background: linear-gradient(to right, transparent, var(--color-gold), transparent);
  opacity: 0.6;
}

/* =============================================
   Body grid
   ============================================= */
.footer__body {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2.5rem;
  padding-top: clamp(3rem, 7vw, 5.5rem);
  padding-bottom: clamp(3rem, 7vw, 5.5rem);
}

@media (min-width: 640px) {
  .footer__body {
    grid-template-columns: 1fr 1fr;
  }
}

@media (min-width: 1024px) {
  .footer__body {
    grid-template-columns: 1.6fr 1fr 1fr 1.2fr;
    gap: 2rem;
  }
}

/* =============================================
   Brand column
   ============================================= */
.footer__brand {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.footer__logo {
  font-family: var(--font-display);
  font-size: 1.875rem;
  font-weight: 400;
  letter-spacing: 0.04em;
  color: var(--color-text);
  display: inline-block;
  transition: color 0.2s ease;
  text-decoration: none;
}

.footer__logo:hover {
  color: var(--color-primary);
}

.footer__logo-accent {
  color: var(--color-gold);
}

.footer__tagline {
  font-family: var(--font-display);
  font-style: italic;
  font-size: 1.125rem;
  font-weight: 400;
  color: var(--color-primary);
  letter-spacing: 0.02em;
}

.footer__desc {
  font-size: 0.875rem;
  font-weight: 300;
  line-height: 1.7;
  color: var(--color-muted);
  max-width: 36ch;
}

/* =============================================
   Link columns
   ============================================= */
.footer__col {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.footer__col-heading {
  font-size: 0.6875rem;
  font-weight: 400;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-text);
}

.footer__links {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.footer__link {
  font-size: 0.875rem;
  font-weight: 300;
  color: var(--color-muted);
  transition: color 0.2s ease;
  display: inline-block;
  cursor: pointer;
  text-decoration: none;
}

.footer__link:hover {
  color: var(--color-primary);
}

.footer__link--static {
  cursor: default;
}

.footer__link--static:hover {
  color: var(--color-muted);
}

.footer__contact-links {
  gap: 0.65rem;
}

/* =============================================
   WhatsApp
   ============================================= */
.footer__whatsapp {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  margin-top: 0.5rem;
  padding: 0.5rem 1rem;
  border: 1px solid var(--color-border);
  color: var(--color-muted);
  font-size: 0.8rem;
  font-weight: 400;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  text-decoration: none;
  transition: color 0.25s ease, border-color 0.25s ease, background-color 0.25s ease;
  align-self: flex-start;
}

.footer__whatsapp:hover {
  color: var(--color-gold);
  border-color: rgba(201, 169, 110, 0.4);
  background-color: rgba(201, 169, 110, 0.05);
}

/* =============================================
   Bottom bar
   ============================================= */
.footer__bottom {
  border-top: 1px solid var(--color-border);
}

.footer__bottom-inner {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  padding-top: 1.5rem;
  padding-bottom: 1.75rem;
}

.footer__copy {
  font-size: 0.8rem;
  font-weight: 300;
  color: var(--color-muted);
  letter-spacing: 0.02em;
}

.footer__mission {
  font-size: 0.8rem;
  font-weight: 300;
  font-style: italic;
  color: #444;
  letter-spacing: 0.02em;
}

@media (min-width: 640px) {
  .footer__bottom-inner {
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }
}
</style>
