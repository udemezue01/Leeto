<script setup>
import { ref } from 'vue'

// Roadmap Phases
const roadmap = [
  {
    phase: 'Phase 01',
    region: 'Nigeria (Launch)',
    status: 'In Progress',
    description: 'Build supply and demand in key Nigerian cities, fine-tune MVP guide onboarding, and validate core booking mechanics.'
  },
  {
    phase: 'Phase 02',
    region: 'Pan-Africa',
    status: 'Upcoming',
    description: 'Expand marketplace infrastructure into major tourism hubs across East, West, and Southern Africa.'
  },
  {
    phase: 'Phase 03',
    region: 'Global Scale',
    status: 'Future Vision',
    description: 'Establish Leeto as the worldwide gig marketplace for authentic local experiences and private custom travel jobs.'
  }
]

// Core Problem vs Solution Cards
const pillars = [
  {
    title: 'The Fragmented Status Quo',
    description: 'Local experts currently rely on scattered channels like Instagram, WhatsApp, travel agencies, or word-of-mouth with zero payment security or reputation tracking.',
    icon: 'M12 9v3.75m-9.303 3.376c-.866 1.5.217 3.374 1.948 3.374h14.71c1.73 0 2.813-1.874 1.948-3.374L13.949 3.378c-.866-1.5-3.032-1.5-3.898 0L2.697 16.126zM12 15.75h.007v.008H12v-.008z'
  },
  {
    title: 'Freelance Economy for Tourism',
    description: 'Just like Fiverr and Upwork democratized digital work, Leeto turns local knowledge into an accessible online service anyone can list and monetize.',
    icon: 'M12 21a9 9 0 100-18 9 9 0 000 18zM12 9v6m-3-3h6'
  },
  {
    title: 'Built-In Trust & Verification',
    description: 'We are engineering rigorous identity checks, secure escrow payments, transparent reviews, and licensing verification to make local guide booking effortless.',
    icon: 'M9 12.75L11.25 15 15 9.75M21 12c0 1.268-.63 2.39-1.593 3.068a3.745 3.745 0 01-1.043 3.296 3.745 3.745 0 01-3.296 1.043A3.745 3.745 0 0112 21c-1.268 0-2.39-.63-3.068-1.593a3.746 3.746 0 01-3.296-1.043 3.745 3.745 0 01-1.043-3.296A3.745 3.745 0 013 12c0-1.268.63-2.39 1.593-3.068a3.745 3.745 0 011.043-3.296 3.746 3.746 0 013.296-1.043A3.746 3.746 0 0112 3c1.268 0 2.39.63 3.068 1.593a3.746 3.746 0 013.296 1.043 3.746 3.746 0 011.043 3.296A3.745 3.745 0 0121 12z'
  }
]
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen">
    
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-16 lg:space-y-24">

      <div class="text-center max-w-3xl mx-auto space-y-6">
        
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-amber-500 animate-pulse"></span>
          Pre-Launch • Currently In Active Development
        </div>

        <h1 class="font-heading text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
          Turning local knowledge into a <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">global gig economy.</span>
        </h1>

        <p class="font-sans text-base sm:text-lg text-zinc-600 font-medium leading-relaxed">
          The internet allowed designers, developers, and writers to sell their digital skills globally. Leeto is building the marketplace infrastructure that lets local experts sell their authentic experiences to travelers worldwide.
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center bg-white p-8 sm:p-12 rounded-3xl border border-zinc-200/80 shadow-xl shadow-zinc-200/50">
        
        <div class="lg:col-span-7 space-y-5">
          <div class="inline-block px-3 py-1 rounded-lg bg-emerald-100 text-emerald-800 text-xs font-bold uppercase tracking-wider">
            Our Story & Origin
          </div>
          <h2 class="font-heading text-2xl sm:text-3xl font-black text-zinc-900 tracking-tight">
            Why does local tourism still feel fragmented?
          </h2>
          <p class="font-sans text-sm sm:text-base text-zinc-600 font-medium leading-relaxed">
            Around the world, millions of passionate locals hold incredible knowledge about their cities—their food, history, hidden alleys, and culture. Yet, becoming an independent tour guide has historically required a massive social following, expensive agency middleman fees, or built-in connections.
          </p>
          <p class="font-sans text-sm sm:text-base text-zinc-600 font-medium leading-relaxed">
            On the other side, travelers struggle to find verified, authentic local guides they can trust. We realized that local tourism is one of the last major skill sectors waiting for a modern, decentralized marketplace.
          </p>
          <div class="p-4 bg-stone-50 rounded-2xl border border-zinc-200/70 text-xs sm:text-sm text-zinc-700 font-semibold italic">
            "We don't believe local experts should need a travel agency or 100k followers just to earn a living sharing their hometown."
          </div>
        </div>

        <div class="lg:col-span-5 bg-zinc-900 text-white p-6 sm:p-8 rounded-2xl border border-zinc-800 space-y-6">
          <h3 class="font-heading text-lg font-bold text-amber-400 uppercase tracking-wider text-xs">The Vision Blueprint</h3>
          <div class="space-y-4 text-xs sm:text-sm text-stone-300 font-sans">
            <div class="flex items-start gap-3">
              <span class="w-6 h-6 rounded-full bg-emerald-500/20 text-emerald-400 flex items-center justify-center font-bold text-xs shrink-0">✓</span>
              <p><strong class="text-white font-bold">Fiverr for Tourism:</strong> Sign up, pass verification, list your experience, set your price, and start receiving direct bookings.</p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-6 h-6 rounded-full bg-emerald-500/20 text-emerald-400 flex items-center justify-center font-bold text-xs shrink-0">✓</span>
              <p><strong class="text-white font-bold">Upwork for Travel:</strong> Travelers post custom itineraries (e.g., <em>"3 days in Lagos for food & nightlife"</em>), and verified local guides submit custom proposals.</p>
            </div>
            <div class="flex items-start gap-3">
              <span class="w-6 h-6 rounded-full bg-emerald-500/20 text-emerald-400 flex items-center justify-center font-bold text-xs shrink-0">✓</span>
              <p><strong class="text-white font-bold">Guide Storefronts:</strong> Every local expert gets an independent profile with ratings, reviews, tour options, and direct payouts.</p>
            </div>
          </div>
        </div>

      </div>

      <div class="space-y-8">
        <div class="text-center max-w-2xl mx-auto">
          <h2 class="font-heading text-2xl sm:text-3xl font-black text-zinc-900 tracking-tight">The Core Problems We Are Solving</h2>
          <p class="font-sans text-sm text-zinc-600 font-medium mt-2">Re-engineering how travelers and local guides interact with modern platform safety.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div 
            v-for="pillar in pillars" 
            :key="pillar.title"
            class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-200 flex flex-col justify-between"
          >
            <div>
              <div class="w-12 h-12 rounded-2xl bg-emerald-100 text-emerald-700 flex items-center justify-center mb-6">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
                  <path stroke-linecap="round" stroke-linejoin="round" :d="pillar.icon" />
                </svg>
              </div>
              <h3 class="font-heading text-lg font-bold text-zinc-900 mb-2">{{ pillar.title }}</h3>
              <p class="font-sans text-xs sm:text-sm text-zinc-600 font-medium leading-relaxed">{{ pillar.description }}</p>
            </div>
          </div>
        </div>
      </div>

      <div class="bg-stone-100 p-8 sm:p-12 rounded-3xl border border-zinc-200/80 text-center space-y-8">
        <div class="max-w-xl mx-auto space-y-2">
          <span class="text-xs font-bold text-emerald-600 uppercase tracking-wider">Growth Mechanics</span>
          <h2 class="font-heading text-2xl sm:text-3xl font-black text-zinc-900 tracking-tight">The Marketplace Flywheel</h2>
          <p class="font-sans text-xs sm:text-sm text-zinc-600 font-medium">As more verified guides list authentic tours, traveler choice expands, generating trust, reviews, and organic marketplace momentum.</p>
        </div>

        <div class="flex flex-wrap items-center justify-center gap-3 text-xs sm:text-sm font-bold text-zinc-800 font-sans">
          <span class="px-4 py-2.5 bg-white rounded-xl shadow-sm border border-zinc-200/70">1. More Local Guides</span>
          <span class="text-emerald-600 font-black">→</span>
          <span class="px-4 py-2.5 bg-white rounded-xl shadow-sm border border-zinc-200/70">2. Diverse Local Tours</span>
          <span class="text-emerald-600 font-black">→</span>
          <span class="px-4 py-2.5 bg-white rounded-xl shadow-sm border border-zinc-200/70">3. More Traveler Choice</span>
          <span class="text-emerald-600 font-black">→</span>
          <span class="px-4 py-2.5 bg-white rounded-xl shadow-sm border border-zinc-200/70">4. Verified Bookings & Reviews</span>
        </div>
      </div>

      <div class="space-y-8">
        <div class="text-center max-w-2xl mx-auto">
          <span class="text-xs font-bold text-amber-900 uppercase tracking-wider bg-amber-100 px-3 py-1 rounded-full">Phased Rollout</span>
          <h2 class="font-heading text-2xl sm:text-3xl font-black text-zinc-900 tracking-tight mt-3">Our Expansion Strategy</h2>
          <p class="font-sans text-sm text-zinc-600 font-medium mt-1">We are starting local, proving the marketplace model, and scaling globally.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div 
            v-for="item in roadmap" 
            :key="item.phase"
            class="bg-white p-6 rounded-2xl border border-zinc-200/80 shadow-md relative overflow-hidden"
          >
            <div class="flex items-center justify-between mb-4">
              <span class="text-xs font-black text-zinc-400 uppercase tracking-widest font-heading">{{ item.phase }}</span>
              <span 
                :class="[
                  'px-2.5 py-0.5 text-[10px] font-bold rounded-full uppercase tracking-wider font-sans',
                  item.status === 'In Progress' ? 'bg-emerald-100 text-emerald-800 border border-emerald-200' : 'bg-stone-100 text-zinc-500'
                ]"
              >
                {{ item.status }}
              </span>
            </div>
            <h3 class="font-heading text-lg font-bold text-zinc-900 mb-2">{{ item.region }}</h3>
            <p class="font-sans text-xs sm:text-sm text-zinc-600 font-medium leading-relaxed">{{ item.description }}</p>
          </div>
        </div>
      </div>

      <div class="bg-zinc-900 rounded-3xl p-8 sm:p-12 text-white relative overflow-hidden shadow-2xl border border-zinc-800">
        <div class="absolute top-0 right-0 -mt-10 -mr-10 w-80 h-80 bg-emerald-500/20 rounded-full blur-3xl pointer-events-none"></div>

        <div class="relative z-10 max-w-3xl space-y-6">
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold uppercase tracking-wider border border-emerald-500/30 font-sans">
            Join the Journey
          </div>
          <h2 class="font-heading text-3xl sm:text-4xl font-black text-white tracking-tight">
            Help us make tourism a global gig economy.
          </h2>
          <p class="font-sans text-stone-300 font-medium text-sm sm:text-base leading-relaxed">
            Leeto is currently in active MVP development. Whether you are an early local guide wanting to pioneer our platform, a traveler interested in early access, or an investor aligned with our vision, we would love to connect.
          </p>

          <div class="pt-4 flex flex-col sm:flex-row items-center gap-4 font-sans">
            <a 
              href="mailto:johnzeus14@gmail.com" 
              class="w-full sm:w-auto px-6 py-3.5 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-sm rounded-xl transition-all duration-200 text-center shadow-lg shadow-emerald-900/40"
            >
              Contact Founding Team
            </a>
            <a 
              href="https://leeto.johnzeus14.workers.dev/" 
              target="_blank"
              class="w-full sm:w-auto px-6 py-3.5 bg-zinc-800 hover:bg-zinc-700 text-stone-200 font-bold text-sm rounded-xl border border-zinc-700 transition-all duration-200 text-center"
            >
              Visit Development Portal
            </a>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>