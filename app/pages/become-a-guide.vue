<script setup>
import { ref } from 'vue'

const fullName = ref('')
const email = ref('')
const city = ref('')
const specialty = ref('food')

const specialties = [
  { value: 'food', label: 'Food & Culinary Tours' },
  { value: 'history', label: 'History & Walking Tours' },
  { value: 'adventure', label: 'Adventure & Outdoors' },
  { value: 'nightlife', label: 'Nightlife & Local Culture' }
]

const steps = [
  {
    number: '01',
    title: 'Submit Application',
    description: 'Tell us about your city, your passion, and the authentic local stories you love to share.'
  },
  {
    number: '02',
    title: 'Identity Verification',
    description: 'Complete our safety check and interview to earn your Verified Local Expert badge.'
  },
  {
    number: '03',
    title: 'Build Tour Offerings',
    description: 'Create custom itineraries highlighting hidden spots, local food, or cultural landmarks.'
  },
  {
    number: '04',
    title: 'Host & Guide Travelers',
    description: 'Accept private booking requests, guide travelers worldwide, and leave lasting memories.'
  }
]

const paymentFeatures = [
  {
    title: 'Set Your Own Rates',
    description: 'Complete pricing autonomy. Set hourly or full-day private tour rates tailored to your experience.'
  },
  {
    title: 'Fast & Direct Payouts',
    description: 'Receive secure direct deposits to your bank account or digital wallet within 24 hours post-tour.'
  },
  {
    title: 'Transparent Earnings',
    description: 'Keep up to 85% of every booking with zero hidden charges or unpredictable platform deductions.'
  },
  {
    title: 'Guaranteed Payments',
    description: 'Travelers pay upfront upon booking. No cash handling or unpaid cancellation worries.'
  }
]

const handleApply = () => {
  if (fullName.value.trim() && email.value.trim() && city.value.trim()) {
    alert(`Application submitted for ${fullName.value} in ${city.value}! We will review your profile shortly.`)
    fullName.value = ''
    email.value = ''
    city.value = ''
  }
}
</script>

<template>
  <div class="bg-stone-50 font-sans text-zinc-900 min-h-screen">
    <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden border-b border-zinc-200/60">
      <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
      <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-8 items-center">
          
          <div class="lg:col-span-7 space-y-8 text-center lg:text-left">
            
            <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider font-sans">
              <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
              Join the Leeto Guide Network
            </div>

            <h1 class="font-heading text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
              Share your city stories, <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">earn on your terms.</span>
            </h1>

            <p class="font-sans text-base sm:text-lg text-zinc-600 max-w-2xl mx-auto lg:mx-0 font-medium leading-relaxed">
              Leeto helps connect travelers with passionate local guides worldwide. Share authentic stories, uncover hidden spots, and build custom private tours on your schedule.
            </p>

            <div class="bg-white p-4 sm:p-6 rounded-2xl sm:rounded-3xl shadow-xl shadow-zinc-200/60 border border-zinc-200/80">
              <form @submit.prevent="handleApply" class="space-y-3 font-sans">
                
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                  <div class="relative flex items-center px-3 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                    <input 
                      v-model="fullName"
                      type="text" 
                      placeholder="Full Name" 
                      required
                      class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-semibold focus:outline-none"
                    />
                  </div>

                  <div class="relative flex items-center px-3 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                    <input 
                      v-model="email"
                      type="email" 
                      placeholder="Email Address" 
                      required
                      class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-semibold focus:outline-none"
                    />
                  </div>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                  <div class="relative flex items-center px-3 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5 text-emerald-600 shrink-0 mr-2.5">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                      <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
                    </svg>
                    <input 
                      v-model="city"
                      type="text" 
                      placeholder="Your City (e.g. Kyoto, Rome)" 
                      required
                      class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-semibold focus:outline-none"
                    />
                  </div>

                  <div class="relative flex items-center px-3 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                    <select 
                      v-model="specialty"
                      class="w-full bg-transparent text-zinc-800 text-sm font-semibold focus:outline-none cursor-pointer"
                    >
                      <option v-for="item in specialties" :key="item.value" :value="item.value">
                        {{ item.label }}
                      </option>
                    </select>
                  </div>
                </div>

                <button 
                  type="submit" 
                  class="w-full px-6 py-3.5 bg-zinc-900 hover:bg-emerald-600 text-white font-bold text-sm rounded-xl shadow-md hover:shadow-emerald-600/20 transition-all duration-200 flex items-center justify-center gap-2 shrink-0 group"
                >
                  <span>Apply to Become a Guide</span>
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4 group-hover:translate-x-0.5 transition-transform">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
                  </svg>
                </button>

              </form>
            </div>

            <div class="flex flex-wrap items-center justify-center lg:justify-start gap-4 sm:gap-6 text-xs text-zinc-500 font-sans font-medium pt-1">
              <span class="font-bold text-zinc-700">Guide Benefits:</span>
              <span> Keep 85% Earnings</span>
              <span>•</span>
              <span>24h Fast Direct Payouts</span>
              <span>•</span>
              <span>100% Flexible Hours</span>
            </div>

          </div>

          <div class="lg:col-span-5 relative">
            <div class="relative bg-white p-3.5 rounded-3xl shadow-2xl border border-zinc-200/80">
              
              <div class="relative h-80 sm:h-96 rounded-2xl overflow-hidden bg-zinc-900">
                <img 
                  src="https://images.unsplash.com/photo-1539635273304-0e56770a8888?auto=format&fit=crop&w=800&q=80" 
                  alt="Local guide hosting travelers" 
                  class="w-full h-full object-cover opacity-90 hover:scale-105 transition-transform duration-500"
                />
                <div class="absolute inset-0 bg-gradient-to-t from-zinc-900/90 via-zinc-900/20 to-transparent"></div>
                
                <div class="absolute top-4 left-4 bg-zinc-900/80 backdrop-blur-md px-3 py-1.5 rounded-full text-white text-xs font-semibold flex items-center gap-2 border border-white/10 font-sans">
                  <span class="relative flex h-2 w-2">
                    <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
                    <span class="relative inline-flex rounded-full h-2 w-2 bg-emerald-500"></span>
                  </span>
                  Accepting Applications
                </div>

                <div class="absolute bottom-4 left-4 right-4 text-white">
                  <p class="text-xs uppercase tracking-widest text-amber-400 font-bold font-sans">Featured Leeto Host</p>
                  <h3 class="font-heading text-xl font-bold">Marco S. — Lisbon, Portugal</h3>
                  <div class="flex items-center gap-1.5 mt-1 text-xs text-stone-200 font-sans">
                    <span class="flex items-center gap-1 text-amber-400 font-bold">
                      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-3.5 h-3.5">
                        <path fill-rule="evenodd" d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005z" clip-rule="evenodd" />
                      </svg>
                      4.99
                    </span>
                    <span>•</span>
                    <span>Avg. $1,250 / month hosting tours</span>
                  </div>
                </div>
              </div>

              <div class="absolute -bottom-5 -left-5 bg-white p-3 rounded-2xl shadow-xl border border-zinc-200/80 hidden sm:flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-amber-100 text-amber-800 flex items-center justify-center">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5">
                    <path stroke-linecap="round" stroke-linejoin="round" d="m3.75 13.5 10.5-11.25L12 10.5h8.25L9.75 21.75 12 13.5H3.75z" />
                  </svg>
                </div>
                <div class="font-sans">
                  <p class="text-xs font-bold text-zinc-900">Direct Weekly Deposits</p>
                  <p class="text-[11px] text-zinc-500">Fast, secure payment payout</p>
                </div>
              </div>

            </div>
          </div>

        </div>
      </div>
    </section>

    <section class="py-12 lg:py-20 relative overflow-hidden border-b border-zinc-200/60 bg-stone-50">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        
        <div class="text-center max-w-2xl mx-auto mb-12">
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider mb-3 font-sans">
            Onboarding Roadmap
          </div>
          <h2 class="font-heading text-3xl sm:text-4xl font-black text-zinc-900 tracking-tight">
            How to become a <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">Leeto Guide</span>
          </h2>
          <p class="font-sans mt-3 text-sm sm:text-base text-zinc-600 font-medium">
            Turn your passion for your city into a flexible income stream in four simple steps.
          </p>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
          <div 
            v-for="step in steps" 
            :key="step.number"
            class="bg-white p-6 rounded-2xl border border-zinc-200/80 shadow-md shadow-zinc-200/40 hover:border-emerald-500/50 transition-all duration-200"
          >
            <div class="font-heading w-10 h-10 rounded-xl bg-amber-100/80 text-amber-900 flex items-center justify-center font-black text-sm mb-4">
              {{ step.number }}
            </div>
            <h3 class="font-heading text-lg font-bold text-zinc-900 mb-2">{{ step.title }}</h3>
            <p class="font-sans text-xs sm:text-sm text-zinc-600 font-medium leading-relaxed">{{ step.description }}</p>
          </div>
        </div>

      </div>
    </section>

    <section class="py-12 lg:py-20 relative overflow-hidden bg-stone-50">
      <div class="absolute bottom-0 right-0 -mb-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>

      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
          
          <div class="lg:col-span-5 space-y-6">
            <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-emerald-100/80 border border-emerald-200/70 text-emerald-900 text-xs font-bold uppercase tracking-wider font-sans">
              Payments & Earnings
            </div>
            <h2 class="font-heading text-3xl sm:text-4xl font-black text-zinc-900 tracking-tight leading-tight">
              Get paid hassle-free, <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">every single time.</span>
            </h2>
            <p class="font-sans text-sm sm:text-base text-zinc-600 font-medium leading-relaxed">
              Leeto handles payment processing, currency conversions, and customer billing so you can focus on leading great experiences.
            </p>

            <div class="bg-white p-5 rounded-2xl border border-zinc-200/80 shadow-lg flex items-start gap-4">
              <div class="w-12 h-12 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center shrink-0">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75m-3-7.036A11.959 11.959 0 0 1 3.598 6 11.99 11.99 0 0 0 3 9.749c0 5.592 3.824 10.29 9 11.623 5.176-1.332 9-6.03 9-11.622 0-1.31-.21-2.571-.598-3.751A11.959 11.959 0 0 1 12 2.714z" />
                </svg>
              </div>
              <div class="font-sans">
                <h4 class="font-heading text-sm font-bold text-zinc-900">Protected Booking System</h4>
                <p class="text-xs text-zinc-600 mt-1 font-medium">
                  All tours are pre-paid by travelers before arrival. Late cancellations are protected under guide payout policies.
                </p>
              </div>
            </div>
          </div>

          <div class="lg:col-span-7 grid grid-cols-1 sm:grid-cols-2 gap-4">
            <div 
              v-for="(feature, idx) in paymentFeatures" 
              :key="idx"
              class="bg-white p-5 rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-lg transition-all"
            >
              <div class="w-3 h-3 rounded-full bg-emerald-500 mb-3"></div>
              <h3 class="font-heading text-base font-bold text-zinc-900 mb-1.5">{{ feature.title }}</h3>
              <p class="font-sans text-xs sm:text-sm text-zinc-600 font-medium leading-relaxed">{{ feature.description }}</p>
            </div>
          </div>

        </div>

      </div>
    </section>
  </div>
</template>