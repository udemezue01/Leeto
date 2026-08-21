<script setup>
import { ref } from 'vue'

const activeTab = ref('travelers')

const verificationSteps = [
  { 
    step: '01', 
    title: 'Government ID Verification', 
    desc: 'Every local guide must submit official government-issued identification to verify their identity before listing tours.' 
  },
  { 
    step: '02', 
    title: 'Background Screening', 
    desc: 'We conduct thorough background checks and public record screenings where legally permitted in host countries.' 
  },
  { 
    step: '03', 
    title: 'Local Knowledge Vetting', 
    desc: 'Our team evaluates guide expertise, proposed routes, and safety protocols to ensure high-quality, secure experiences.' 
  },
  { 
    step: '04', 
    title: 'Continuous Review Audits', 
    desc: 'Guide ratings and traveler feedback are monitored automatically. Ratings falling below 4.7 are flagged for review.' 
  }
]

const travelerTips = [
  'Keep all communication and booking payments strictly within the Leeto platform for buyer protection.',
  'Share your live itinerary and guide details with a trusted family member or friend prior to your tour.',
  'Check guide reviews, past traveler photos, and verified badges before finalizing your reservation.',
  'Trust your instincts and reach out to our 24/7 safety team immediately if a situation feels uncomfortable.'
]

const guideTips = [
  'Arrange initial traveler meetups in well-lit, recognizable public locations.',
  'Keep your route and timeline updated in the app so our safety system can track active bookings.',
  'Brief travelers on terrain, weather conditions, and physical requirements before starting the tour.',
  'Report any guest misconduct or policy violations to Leeto Support without hesitation.'
]
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen text-zinc-900">
    
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-16">

      <div class="text-center max-w-3xl mx-auto space-y-4">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-emerald-100/80 border border-emerald-200/70 text-emerald-900 text-xs font-heading font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-emerald-500"></span>
          Trust & Security Center
        </div>

        <h1 class="font-heading text-4xl sm:text-5xl font-black text-zinc-900 tracking-tight leading-[1.15]">
          Your safety is <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">our top priority.</span>
        </h1>

        <p class="font-sans text-base sm:text-lg text-zinc-600 font-medium leading-relaxed">
          We build rigorous standards, identity verification, and 24/7 support into every experience so you can explore with complete confidence.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        
        <div class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4 relative overflow-hidden">
          <div class="w-12 h-12 rounded-2xl bg-emerald-100 text-emerald-700 flex items-center justify-center shrink-0">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75m-3-7.036A11.959 11.959 0 013.598 6 11.99 11.99 0 003 9.749c0 5.592 3.824 10.29 9 11.623 5.176-1.332 9-6.03 9-11.622 0-1.31-.21-2.571-.598-3.751h-.152c-3.196 0-6.1-1.248-8.25-3.285z" />
            </svg>
          </div>
          <h3 class="font-heading text-xl font-bold text-zinc-900">100% Verified Guides</h3>
          <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
            Every host undergoes mandatory identity checks and background screening before publishing their first tour.
          </p>
        </div>

        <div class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4 relative overflow-hidden">
          <div class="w-12 h-12 rounded-2xl bg-amber-100 text-amber-800 flex items-center justify-center shrink-0">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="M16.5 10.5V6.75a4.5 4.5 0 10-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 002.25-2.25v-6.75a2.25 2.25 0 00-2.25-2.25H6.75a2.25 2.25 0 00-2.25 2.25v6.75a2.25 2.25 0 002.25 2.25z" />
            </svg>
          </div>
          <h3 class="font-heading text-xl font-bold text-zinc-900">Protected Payments</h3>
          <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
            Transactions are encrypted and held securely. Guide payouts are only released 24 hours after a tour finishes safely.
          </p>
        </div>

        <div class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4 relative overflow-hidden">
          <div class="w-12 h-12 rounded-2xl bg-stone-100 text-zinc-800 flex items-center justify-center shrink-0">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6 text-emerald-600">
              <path stroke-linecap="round" stroke-linejoin="round" d="M14.25 9.75v-4.5m0 4.5h4.5m-4.5 0l6-6m-3 18c-3.728 0-7.033-1.002-9.84-2.753A1.98 1.98 0 013 18.271V15.75c0-.898.59-1.68 1.455-1.916l3.19-0.87a1.98 1.98 0 012.083.65l1.65 2.2a15.42 15.42 0 006.183-6.183l-2.2-1.65a1.98 1.98 0 01-.65-2.083l.87-3.19A1.98 1.98 0 0115.75 3h2.521c.91 0 1.693.62 1.895 1.507A19.53 19.53 0 0121 12c0 4.97-1.8 9.518-4.75 13.003z" />
            </svg>
          </div>
          <h3 class="font-heading text-xl font-bold text-zinc-900">24/7 Incident Support</h3>
          <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
            Our dedicated trust and safety team operates around the clock to assist with active booking emergencies or concerns.
          </p>
        </div>

      </div>

      <div class="bg-white p-6 sm:p-10 rounded-3xl border border-zinc-200/80 shadow-xl space-y-8">
        <div class="max-w-2xl space-y-2">
          <p class="font-heading text-xs font-bold text-emerald-600 uppercase tracking-wider">Multi-Stage Screening</p>
          <h2 class="font-heading text-2xl sm:text-3xl font-black text-zinc-900">How We Verify Local Guides</h2>
          <p class="font-sans text-sm text-zinc-600 font-medium">Before any guide can lead a tour, they pass through our 4-step verification framework.</p>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
          <div v-for="item in verificationSteps" :key="item.step" class="bg-stone-50 p-5 rounded-2xl border border-zinc-200/70 space-y-3">
            <span class="font-heading text-2xl font-black text-emerald-600">{{ item.step }}</span>
            <h4 class="font-heading text-base font-bold text-zinc-900">{{ item.title }}</h4>
            <p class="font-sans text-xs text-zinc-600 font-medium leading-relaxed">{{ item.desc }}</p>
          </div>
        </div>
      </div>

      <div class="space-y-6">
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4">
          <div>
            <h2 class="font-heading text-2xl sm:text-3xl font-black text-zinc-900">Safety Guidelines</h2>
            <p class="font-sans text-sm text-zinc-600 font-medium">Practical recommendations for every step of your journey.</p>
          </div>

          <div class="inline-flex p-1 bg-stone-200/80 rounded-2xl shrink-0">
            <button 
              @click="activeTab = 'travelers'"
              class="px-4 py-2 rounded-xl text-xs font-heading font-bold transition-all"
              :class="activeTab === 'travelers' ? 'bg-zinc-900 text-white shadow-md' : 'text-zinc-600 hover:text-zinc-900'"
            >
              For Travelers
            </button>
            <button 
              @click="activeTab = 'guides'"
              class="px-4 py-2 rounded-xl text-xs font-heading font-bold transition-all"
              :class="activeTab === 'guides' ? 'bg-zinc-900 text-white shadow-md' : 'text-zinc-600 hover:text-zinc-900'"
            >
              For Local Guides
            </button>
          </div>
        </div>

        <div v-if="activeTab === 'travelers'" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md">
          <ul class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <li v-for="(tip, idx) in travelerTips" :key="idx" class="flex items-start gap-3 p-4 bg-stone-50 rounded-2xl border border-zinc-200/60">
              <span class="w-6 h-6 rounded-full bg-emerald-100 text-emerald-700 font-heading font-bold text-xs flex items-center justify-center shrink-0 mt-0.5">✓</span>
              <p class="font-sans text-sm text-zinc-700 font-medium leading-relaxed">{{ tip }}</p>
            </li>
          </ul>
        </div>

        <div v-if="activeTab === 'guides'" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md">
          <ul class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <li v-for="(tip, idx) in guideTips" :key="idx" class="flex items-start gap-3 p-4 bg-stone-50 rounded-2xl border border-zinc-200/60">
              <span class="w-6 h-6 rounded-full bg-amber-100 text-amber-800 font-heading font-bold text-xs flex items-center justify-center shrink-0 mt-0.5">✓</span>
              <p class="font-sans text-sm text-zinc-700 font-medium leading-relaxed">{{ tip }}</p>
            </li>
          </ul>
        </div>
      </div>

      <div class="bg-zinc-900 text-white p-6 sm:p-10 rounded-3xl shadow-2xl border border-zinc-800 flex flex-col lg:flex-row lg:items-center justify-between gap-8 relative overflow-hidden">
        <div class="space-y-2 relative z-10 max-w-xl">
          <span class="font-heading text-xs font-bold text-amber-400 uppercase tracking-wider">Need Urgent Assistance?</span>
          <h3 class="font-heading text-2xl sm:text-3xl font-black text-white">24/7 Safety Dispatch & Support</h3>
          <p class="font-sans text-sm text-stone-300 font-medium leading-relaxed">
            If you are currently on an active tour and require immediate safety intervention or emergency aid, our response team is standing by.
          </p>
        </div>

        <div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-4 relative z-10 shrink-0">
          <a 
            href="tel:+18005550199" 
            class="font-heading px-6 py-3.5 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-xs rounded-xl shadow-md transition-all flex items-center justify-center gap-2"
          >
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
              <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-2.826-1.07-5.02-3.264-6.09-6.09l1.293-.97c.362-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z" />
            </svg>
            <span>Emergency Line</span>
          </a>

          <a 
            href="mailto:safety@leeto.com" 
            class="font-heading px-6 py-3.5 bg-stone-800 hover:bg-stone-700 text-stone-200 font-bold text-xs rounded-xl border border-stone-700 transition-all flex items-center justify-center gap-2"
          >
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
              <path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" />
            </svg>
            <span>Email Safety Team</span>
          </a>
        </div>
      </div>

    </div>
  </section>
</template>