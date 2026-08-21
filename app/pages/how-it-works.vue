<script setup>
import { ref } from 'vue'

// Role state toggle
const activeRole = ref('travelers') // 'travelers' | 'guides'

// How it works steps data
const travelerSteps = [
  {
    step: '01',
    title: 'Discover Local Guides',
    description: 'Browse verified local experts worldwide. Filter by city, interests, or travel category to find your ideal host.',
    icon: 'M15 10.5a3 3 0 11-6 0 3 3 0 016 0z M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z'
  },
  {
    step: '02',
    title: 'Customize Your Itinerary',
    description: 'Message guides directly to personalize your private tour. Adjust pacing, request hidden spots, or tailor for dietary preferences.',
    icon: 'M8.625 12a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0H8.25m4.125 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0H12m4.125 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0h-.375M21 12c0 4.556-4.03 8.25-9 8.25a9.764 9.764 0 01-2.555-.337A5.972 5.972 0 015.41 20.97a.75.75 0 01-.81-.54 5.96 5.96 0 011.207-3.056C4.41 15.82 3 14.02 3 12c0-4.556 4.03-8.25 9-8.25s9 3.694 9 8.25z'
  },
  {
    step: '03',
    title: 'Book Safely & Explore',
    description: 'Pay securely on Leeto. Meet your guide for an authentic, off-the-beaten-path experience with full peace of mind.',
    icon: 'M9 12.75L11.25 15 15 9.75M21 12c0 1.268-.63 2.39-1.593 3.068a3.745 3.745 0 01-1.043 3.296 3.745 3.745 0 01-3.296 1.043A3.745 3.745 0 0112 21c-1.268 0-2.39-.63-3.068-1.593a3.746 3.746 0 01-3.296-1.043 3.745 3.745 0 01-1.043-3.296A3.745 3.745 0 013 12c0-1.268.63-2.39 1.593-3.068a3.745 3.745 0 011.043-3.296 3.746 3.746 0 013.296-1.043A3.746 3.746 0 0112 3c1.268 0 2.39.63 3.068 1.593a3.746 3.746 0 013.296 1.043 3.746 3.746 0 011.043 3.296A3.745 3.745 0 0121 12z'
  }
]

const guideSteps = [
  {
    step: '01',
    title: 'Apply & Get Verified',
    description: 'Sign up and complete our verification check. Share your passion, local expertise, and authentic story ideas.',
    icon: 'M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.501 20.118a7.5 7.5 0 0114.998 0A17.933 17.933 0 0112 21.75c-2.676 0-5.216-.584-7.499-1.632z'
  },
  {
    step: '02',
    title: 'List Your Experiences',
    description: 'Set your own availability, itinerary, group sizes, and tour rates with total creative freedom.',
    icon: 'M10.5 6a7.5 7.5 0 107.5 7.5h-7.5V6z'
  },
  {
    step: '03',
    title: 'Host & Earn Direct',
    description: 'Guide travelers through your city and get automatic payouts directly to your account post-tour.',
    icon: 'M2.25 18.75a60.07 60.07 0 0115.797 2.101c.727.198 1.453-.342 1.453-1.096V18.75M3.75 4.5h16.5a1.5 1.5 0 011.5 1.5v9a1.5 1.5 0 01-1.5 1.5H3.75a1.5 1.5 0 01-1.5-1.5v-9a1.5 1.5 0 011.5-1.5z'
  }
]

const payoutFeatures = [
  {
    title: 'Automatic Direct Deposits',
    description: 'Earnings are automatically released 24 hours after successfully completing each tour experience.',
    badge: 'Fast Payouts'
  },
  {
    title: 'Keep Up to 85%+',
    description: 'Transparent pricing with no hidden listing fees. You set your rates, and we process payments securely.',
    badge: 'Fair Earnings'
  },
  {
    title: 'Guaranteed Payments',
    description: 'Travelers pay upfront. Late cancellations within protection windows are fully covered.',
    badge: 'Fraud Protected'
  }
]
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60">
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-16 lg:space-y-24">
      
      <div class="text-center max-w-3xl mx-auto space-y-6">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider font-sans">
          <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
          Simple, Transparent & Secure
        </div>

        <h1 class="font-heading text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
          How Leeto works for <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">everyone.</span>
        </h1>

        <p class="font-sans text-base sm:text-lg text-zinc-600 font-medium leading-relaxed">
          Whether you want to explore hidden corners of the world or share your passion for your hometown, Leeto makes connecting seamless and rewarding.
        </p>

        <div class="inline-flex p-1.5 bg-stone-200/70 rounded-2xl border border-zinc-200/80 shadow-inner">
          <button
            @click="activeRole = 'travelers'"
            :class="[
              'px-6 py-2.5 rounded-xl font-sans font-bold text-sm transition-all duration-200',
              activeRole === 'travelers' 
                ? 'bg-white text-zinc-900 shadow-md' 
                : 'text-zinc-600 hover:text-zinc-900'
            ]"
          >
            For Travelers
          </button>
          <button
            @click="activeRole = 'guides'"
            :class="[
              'px-6 py-2.5 rounded-xl font-sans font-bold text-sm transition-all duration-200',
              activeRole === 'guides' 
                ? 'bg-white text-zinc-900 shadow-md' 
                : 'text-zinc-600 hover:text-zinc-900'
            ]"
          >
            For Local Guides
          </button>
        </div>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div 
          v-for="step in (activeRole === 'travelers' ? travelerSteps : guideSteps)" 
          :key="step.step"
          class="relative bg-white p-6 sm:p-8 rounded-2xl sm:rounded-3xl shadow-xl shadow-zinc-200/60 border border-zinc-200/80 flex flex-col justify-between group hover:-translate-y-1 transition-all duration-200"
        >
          <div>
            <div class="flex items-center justify-between mb-6">
              <span class="w-12 h-12 rounded-2xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-heading font-black text-lg">
                {{ step.step }}
              </span>
              <div class="w-10 h-10 rounded-xl bg-stone-50 border border-zinc-200/70 flex items-center justify-center text-zinc-500 group-hover:text-emerald-600 group-hover:border-emerald-600 transition-colors">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5">
                  <path stroke-linecap="round" stroke-linejoin="round" :d="step.icon" />
                </svg>
              </div>
            </div>

            <h3 class="font-heading text-xl font-bold text-zinc-900 mb-2">{{ step.title }}</h3>
            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">{{ step.description }}</p>
          </div>
        </div>
      </div>

      <div class="bg-zinc-900 rounded-3xl p-6 sm:p-10 lg:p-12 text-white relative overflow-hidden shadow-2xl border border-zinc-800">
        <div class="absolute top-0 right-0 -mt-10 -mr-10 w-80 h-80 bg-emerald-500/20 rounded-full blur-3xl pointer-events-none"></div>
        
        <div class="relative z-10 max-w-3xl mb-10">
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold uppercase tracking-wider mb-4 border border-emerald-500/30 font-sans">
            Seamless Payouts
          </div>
          <h2 class="font-heading text-3xl sm:text-4xl font-black text-white tracking-tight">
            How earnings & payouts work for Guides
          </h2>
          <p class="font-sans text-stone-300 font-medium text-sm sm:text-base mt-3">
            Focus on creating memorable experiences. We take care of secure booking payments, fraud protection, and fast direct transfers.
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 relative z-10">
          <div 
            v-for="payout in payoutFeatures" 
            :key="payout.title" 
            class="bg-zinc-800/80 backdrop-blur-md p-6 rounded-2xl border border-zinc-700/60"
          >
            <span class="inline-block px-2.5 py-1 rounded-lg bg-amber-500/20 text-amber-300 text-xs font-bold mb-3 font-sans">
              {{ payout.badge }}
            </span>
            <h4 class="font-heading text-lg font-bold text-white mb-2">{{ payout.title }}</h4>
            <p class="font-sans text-xs sm:text-sm text-stone-300 font-medium leading-relaxed">{{ payout.description }}</p>
          </div>
        </div>

        <div class="mt-10 pt-8 border-t border-zinc-800 flex flex-col sm:flex-row items-center justify-between gap-4 relative z-10">
          <div class="text-center sm:text-left">
            <p class="font-heading text-base font-bold text-white">Ready to share your city with global travelers?</p>
            <p class="font-sans text-xs text-stone-400">Join our growing network of verified local guides today.</p>
          </div>
          <button class="w-full sm:w-auto px-6 py-3 bg-emerald-600 hover:bg-emerald-500 text-white font-sans font-bold text-sm rounded-xl shadow-lg transition-all duration-200 shrink-0">
            Become a Guide Now
          </button>
        </div>
      </div>

    </div>
  </section>
</template>