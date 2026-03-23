<script setup>
import { reactive, ref, onMounted } from 'vue'

const sectionRef = ref(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.15 }
  )
  observer.observe(sectionRef.value)
})

const contactDetails = [
  {
    icon: `<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>`,
    label: 'coromandelbranding@gmail.com',
  },
  {
    icon: `<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/></svg>`,
    label: '+91 82489 20182',
  },
  {
    icon: `<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>`,
    label: 'Auroville, Tamil Nadu',
  },
]

const form = reactive({
  name: '',
  phone: '',
  business: '',
  message: '',
})

const errors = reactive({
  name: '',
  phone: '',
  message: '',
})

const submitted = ref(false)

function validate() {
  errors.name    = form.name.trim()    ? '' : 'Your name is required.'
  errors.phone   = form.phone.trim()   ? '' : 'Phone number is required.'
  errors.message = form.message.trim() ? '' : 'Please tell us about your business.'
  return !errors.name && !errors.phone && !errors.message
}

function handleSubmit() {
  if (!validate()) return

  // Construct WhatsApp message
  const whatsappMessage = `*New Enquiry from Website*
  
*Name:* ${form.name}
*Phone:* ${form.phone}
${form.business ? `*Business:* ${form.business}` : ''}
*Message:* ${form.message}`

  const encodedMessage = encodeURIComponent(whatsappMessage)
  const whatsappUrl = `https://wa.me/918248920182?text=${encodedMessage}`

  // Open WhatsApp in a new tab
  window.open(whatsappUrl, '_blank')

  submitted.value = true
}

function resetForm() {
  form.name = form.phone = form.business = form.message = ''
  errors.name = errors.phone = errors.message = ''
  submitted.value = false
}
</script>

<template>
  <section class="contact section-hidden" :class="{ 'section-visible': visible }" id="contact" ref="sectionRef">
    <div class="contact__inner container">

      <!-- Left: info -->
      <div class="contact__info">
        <p class="contact__label">Get In Touch</p>

        <h2 class="contact__heading">Ready to <em>get found?</em></h2>

        <p class="contact__sub">
          Tell us about your business and goals. We'll respond within 24 hours
          with a clear plan — no jargon, no pressure.
        </p>

        <ul class="contact__details">
          <li
            v-for="detail in contactDetails"
            :key="detail.label"
            class="contact__detail"
          >
            <span class="contact__detail-icon" v-html="detail.icon" aria-hidden="true"></span>
            <span class="contact__detail-text">{{ detail.label }}</span>
          </li>
        </ul>

        <!-- WhatsApp direct -->
        <a href="https://wa.me/918248920182" target="_blank" rel="noopener" class="contact__whatsapp">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413z"/></svg>
          Chat on WhatsApp
        </a>
      </div>

      <!-- Right: form -->
      <div class="contact__form-wrap">
        <!-- Success state -->
        <div v-if="submitted" class="contact__success">
          <svg class="contact__success-icon" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><polyline points="22 4 12 14.01 9 11.01"/></svg>
          <p class="contact__success-msg">
            Your message has been sent. We'll be in touch within 24 hours.
          </p>
          <button class="contact__reset" @click="resetForm">Send another message</button>
        </div>

        <!-- Form -->
        <form v-else class="contact__form" novalidate @submit.prevent="handleSubmit">
          <div class="form-row">
            <!-- Name -->
            <div class="form-field" :class="{ 'form-field--error': errors.name }">
              <label class="form-label" for="name">Your Name</label>
              <input
                id="name"
                v-model="form.name"
                class="form-input"
                type="text"
                placeholder="Rajesh Kumar"
                autocomplete="name"
                @blur="errors.name = form.name.trim() ? '' : 'Your name is required.'"
              />
              <p v-if="errors.name" class="form-error" role="alert">{{ errors.name }}</p>
            </div>

            <!-- Phone -->
            <div class="form-field" :class="{ 'form-field--error': errors.phone }">
              <label class="form-label" for="phone">Phone Number</label>
              <input
                id="phone"
                v-model="form.phone"
                class="form-input"
                type="tel"
                placeholder="+91 95005 11297"
                autocomplete="tel"
                @blur="errors.phone = form.phone.trim() ? '' : 'Phone number is required.'"
              />
              <p v-if="errors.phone" class="form-error" role="alert">{{ errors.phone }}</p>
            </div>
          </div>

          <!-- Business Name -->
          <div class="form-field">
            <label class="form-label" for="business">
              Business Name <span class="form-label-optional">(optional)</span>
            </label>
            <input
              id="business"
              v-model="form.business"
              class="form-input"
              type="text"
              placeholder="Your shop, clinic, or business name"
              autocomplete="organization"
            />
          </div>

          <!-- Message -->
          <div class="form-field" :class="{ 'form-field--error': errors.message }">
            <label class="form-label" for="message">Tell Us About Your Business</label>
            <textarea
              id="message"
              v-model="form.message"
              class="form-input form-textarea"
              placeholder="What do you do, where are you located, and what's your biggest challenge getting customers online?"
              rows="5"
              @blur="errors.message = form.message.trim() ? '' : 'Please tell us about your business.'"
            ></textarea>
            <p v-if="errors.message" class="form-error" role="alert">{{ errors.message }}</p>
          </div>

          <button type="submit" class="form-submit">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
            Send Enquiry
          </button>
        </form>
      </div>

    </div>
  </section>
</template>

<style scoped>
/* =============================================
   Section
   ============================================= */
.contact {
  background-color: var(--color-surface);
  padding-block: var(--section-padding);
  position: relative;
}

.contact::before {
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
.contact__inner {
  display: grid;
  grid-template-columns: 1fr;
  gap: clamp(3rem, 7vw, 6rem);
  align-items: start;
}

@media (min-width: 900px) {
  .contact__inner {
    grid-template-columns: 1fr 1.2fr;
  }
}

/* =============================================
   Info (left)
   ============================================= */
.contact__info {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.contact__label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--color-gold);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.contact__label::before {
  content: '';
  display: inline-block;
  width: 2rem;
  height: 1px;
  background-color: var(--color-gold);
  flex-shrink: 0;
}

.contact__heading {
  font-family: var(--font-display);
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 400;
  line-height: 1.1;
  color: var(--color-text);
  letter-spacing: -0.01em;
}

.contact__heading em {
  font-style: italic;
  color: var(--color-primary);
}

.contact__sub {
  font-size: 0.9375rem;
  font-weight: 300;
  line-height: 1.75;
  color: var(--color-muted);
  max-width: 38ch;
}

/* Contact details list */
.contact__details {
  display: flex;
  flex-direction: column;
  gap: 1.1rem;
  padding-top: 0.5rem;
}

.contact__detail {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.contact__detail-icon {
  color: var(--color-gold);
  flex-shrink: 0;
  opacity: 0.85;
}

.contact__detail-text {
  font-size: 0.9rem;
  font-weight: 300;
  color: var(--color-muted);
  letter-spacing: 0.02em;
}

/* WhatsApp link */
.contact__whatsapp {
  display: inline-flex;
  align-items: center;
  gap: 0.65rem;
  font-size: 0.8rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--color-gold);
  border: 1px solid var(--color-gold);
  padding: 0.7rem 1.5rem;
  align-self: flex-start;
  transition: background-color 0.25s ease, color 0.25s ease;
}

.contact__whatsapp:hover {
  background-color: var(--color-gold);
  color: var(--color-bg);
}

/* =============================================
   Form wrapper
   ============================================= */
.contact__form-wrap {
  background-color: var(--color-bg);
  border: 1px solid var(--color-border);
  padding: clamp(1.75rem, 4vw, 2.75rem);
}

/* =============================================
   Form
   ============================================= */
.contact__form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
}

@media (min-width: 540px) {
  .form-row {
    grid-template-columns: 1fr 1fr;
  }
}

.form-field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-label {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--color-muted);
}

.form-label-optional {
  color: #444;
  text-transform: none;
  letter-spacing: 0;
  font-size: 0.7rem;
}

.form-input {
  background-color: var(--color-surface);
  border: 1px solid var(--color-border);
  color: var(--color-text);
  font-family: var(--font-body);
  font-size: 0.9rem;
  font-weight: 300;
  padding: 0.8rem 1rem;
  outline: none;
  transition: border-color 0.25s ease;
  width: 100%;
}

.form-input::placeholder {
  color: #3a3a3a;
}

.form-input:focus {
  border-color: rgba(201, 169, 110, 0.5);
}

.form-field--error .form-input {
  border-color: rgba(200, 80, 80, 0.5);
}

.form-textarea {
  resize: vertical;
  min-height: 8rem;
  line-height: 1.6;
}

.form-error {
  font-size: 0.75rem;
  color: #c85050;
  letter-spacing: 0.02em;
}

/* Submit */
.form-submit {
  display: inline-flex;
  align-items: center;
  gap: 0.65rem;
  font-size: 0.8rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--color-bg);
  background-color: var(--color-gold);
  border: 1px solid var(--color-gold);
  padding: 0.9rem 2.25rem;
  cursor: pointer;
  align-self: flex-start;
  transition: background-color 0.25s ease, border-color 0.25s ease, color 0.25s ease;
}

.form-submit:hover {
  background-color: var(--color-primary);
  border-color: var(--color-primary);
}

/* =============================================
   Success state
   ============================================= */
.contact__success {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 1.25rem;
  padding: 1rem 0;
}

.contact__success-icon {
  color: var(--color-gold);
}

.contact__success-msg {
  font-family: var(--font-display);
  font-style: italic;
  font-size: clamp(1.25rem, 2.5vw, 1.625rem);
  font-weight: 400;
  line-height: 1.45;
  color: var(--color-text);
  max-width: 36ch;
}

.contact__reset {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--color-muted);
  border-bottom: 1px solid var(--color-border);
  padding-bottom: 2px;
  cursor: pointer;
  background: none;
  border-top: none;
  border-left: none;
  border-right: none;
  transition: color 0.2s ease, border-color 0.2s ease;
}

.contact__reset:hover {
  color: var(--color-text);
  border-bottom-color: var(--color-muted);
}
</style>
