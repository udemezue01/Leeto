<script setup>
import { ref } from 'vue'

const lastUpdated = 'August 21, 2026'

const activeSection = ref('overview')

const sections = [
  { id: 'overview', title: '1. Overview & Platform Role' },
  { id: 'eligibility', title: '2. Account & Eligibility' },
  { id: 'travelers', title: '3. Traveler Terms & Bookings' },
  { id: 'guides', title: '4. Local Guide Responsibilities' },
  { id: 'payments', title: '5. Fees, Earnings & Payouts' },
  { id: 'cancellations', title: '6. Cancellations & Refunds' },
  { id: 'safety', title: '7. Safety & Background Checks' },
  { id: 'liability', title: '8. Limitation of Liability' },
  { id: 'disputes', title: '9. Disputes & Governing Law' }
]

const scrollToSection = (id) => {
  activeSection.value = id
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen text-zinc-900">
    
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-12">

      <div class="text-center max-w-3xl mx-auto space-y-4">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-heading font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
          Legal & Transparency
        </div>

        <h1 class="font-heading text-4xl sm:text-5xl font-black text-zinc-900 tracking-tight leading-[1.15]">
          Leeto <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">Terms of Service</span>
        </h1>

        <p class="font-sans text-xs sm:text-sm font-semibold text-zinc-500">
          Last Updated: <span class="text-zinc-800">{{ lastUpdated }}</span>
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-start">

        <aside class="lg:col-span-4 sticky top-6 z-20">
          <div class="bg-white p-5 rounded-3xl border border-zinc-200/80 shadow-xl shadow-zinc-200/50 space-y-3">
            <p class="font-heading text-xs font-bold text-zinc-400 uppercase tracking-wider px-2">Table of Contents</p>
            <nav class="space-y-1">
              <button
                v-for="item in sections"
                :key="item.id"
                @click="scrollToSection(item.id)"
                :class="[
                  'w-full text-left px-3 py-2 rounded-xl font-sans text-xs font-bold transition-all duration-200 flex items-center justify-between',
                  activeSection === item.id 
                    ? 'bg-zinc-900 text-white shadow-md' 
                    : 'text-zinc-600 hover:bg-stone-100 hover:text-zinc-900'
                ]"
              >
                <span>{{ item.title }}</span>
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-3.5 h-3.5 opacity-60">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
                </svg>
              </button>
            </nav>
          </div>
        </aside>

        <main class="lg:col-span-8 space-y-8">
          
          <article id="overview" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="font-heading text-xl font-black text-zinc-900">1. Overview & Platform Role</h2>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              Leeto provides an online marketplace connecting independent local guides ("Guides") with travelers ("Travelers") seeking authentic, personalized tours and experiences worldwide. 
            </p>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              Leeto does not own, create, manage, or control any tour experiences. Guides operate as independent contractors, and Leeto acts purely as an intermediary facilitating discovery, communication, and secure payment handling.
            </p>
          </article>

          <article id="eligibility" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="font-heading text-xl font-black text-zinc-900">2. Account Registration & Eligibility</h2>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              To use Leeto, you must be at least 18 years old and capable of entering into legally binding contracts. When creating an account, you agree to provide accurate, current, and complete information.
            </p>
            <ul class="font-sans list-disc list-inside text-sm text-zinc-600 font-medium space-y-2 pl-2">
              <li>You are responsible for safeguarding your login credentials.</li>
              <li>You must notify Leeto immediately of any unauthorized account activity.</li>
              <li>Accounts cannot be transferred or sold to third parties without prior authorization.</li>
            </ul>
          </article>

          <article id="travelers" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="font-heading text-xl font-black text-zinc-900">3. Traveler Terms & Bookings</h2>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              When a Traveler books a tour on Leeto, they enter into a direct contractual agreement with the selected Guide. Travelers agree to read tour listings thoroughly, respect local regulations, and adhere to agreed meeting times.
            </p>
          </article>

          <article id="guides" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="font-heading text-xl font-black text-zinc-900">4. Local Guide Responsibilities</h2>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              Guides represent themselves accurately and guarantee that listed tours comply with local laws, municipal permits, and safety standards.
            </p>
            <div class="bg-stone-50 p-4 rounded-2xl border border-zinc-200/70 text-xs text-zinc-700 font-medium leading-relaxed">
              <strong class="font-heading font-bold text-zinc-900">Notice for Guides:</strong> Guides are strictly independent providers and are not employees, partners, or agents of Leeto. Guides are responsible for reporting and paying their own income and municipal taxes.
            </div>
          </article>

          <article id="payments" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="font-heading text-xl font-black text-zinc-900">5. Fees, Earnings & Direct Payouts</h2>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              Leeto processes all booking transactions securely. Travelers pay total fees at the time of booking confirmation.
            </p>
            <ul class="font-sans list-disc list-inside text-sm text-zinc-600 font-medium space-y-2 pl-2">
              <li><strong class="font-heading text-zinc-900">Platform Service Fee:</strong> Leeto retains a platform service fee deducted from the tour total.</li>
              <li><strong class="font-heading text-zinc-900">Guide Earnings:</strong> Payouts are automatically initiated 24 hours after a tour is completed successfully.</li>
            </ul>
          </article>

          <article id="cancellations" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="font-heading text-xl font-black text-zinc-900">6. Cancellations & Refund Policy</h2>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div class="bg-emerald-50/60 p-4 rounded-2xl border border-emerald-200/60">
                <p class="font-heading text-xs font-bold text-emerald-900 uppercase">24-Hour Full Refund</p>
                <p class="font-sans text-xs text-emerald-800 font-medium mt-1">Travelers receive a 100% refund for cancellations made up to 24 hours prior to tour start time.</p>
              </div>
              <div class="bg-amber-50/60 p-4 rounded-2xl border border-amber-200/60">
                <p class="font-heading text-xs font-bold text-amber-900 uppercase">Late Cancellations</p>
                <p class="font-sans text-xs text-amber-800 font-medium mt-1">Cancellations within 24 hours are non-refundable to ensure fair compensation for host preparation.</p>
              </div>
            </div>
          </article>

          <article id="safety" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="font-heading text-xl font-black text-zinc-900">7. Safety & Background Verification</h2>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              Leeto conducts identity verification and background screenings on Guides where legally permitted. However, users are encouraged to exercise personal caution, inspect guide reviews, and utilize Leeto’s in-app messaging.
            </p>
          </article>

          <article id="liability" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="font-heading text-xl font-black text-zinc-900">8. Limitation of Liability</h2>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              To the maximum extent permitted by applicable law, Leeto is not liable for indirect, incidental, or consequential damages resulting from tour participation, guide misconduct, or personal injuries incurred during experiences.
            </p>
          </article>

          <article id="disputes" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="font-heading text-xl font-black text-zinc-900">9. Dispute Resolution & Governing Law</h2>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              These Terms are governed by international commercial law standards. Any disputes or claims arising out of or in connection with Leeto services shall first be submitted to Leeto Support for informal resolution prior to formal arbitration.
            </p>
          </article>

          <div class="bg-zinc-900 text-white p-6 sm:p-8 rounded-3xl shadow-xl flex flex-col sm:flex-row items-center justify-between gap-6 border border-zinc-800">
            <div>
              <p class="font-heading text-xs font-bold text-amber-400 uppercase tracking-wider">Have legal questions?</p>
              <h3 class="font-heading text-xl font-black text-white mt-1">Contact Leeto Legal Team</h3>
              <p class="font-sans text-xs text-stone-300 font-medium mt-1">Reach out for clarification on terms, partner agreements, or privacy matters.</p>
            </div>
            <a href="mailto:legal@leeto.com" class="font-sans px-6 py-3 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-xs rounded-xl shadow-md transition-all shrink-0">
              legal@leeto.com
            </a>
          </div>

        </main>
      </div>

    </div>
  </section>
</template>