<script setup>
import { ref } from 'vue'

const searchQuery = ref('')

const handleSearch = () => {
  if (searchQuery.value.trim()) {
    console.log('Searching for destination:', searchQuery.value)
  }
}
</script>

<template>
  <section class="font-sans relative overflow-hidden bg-gradient-to-br from-emerald-500 via-teal-500 to-emerald-600 py-16 sm:py-24 text-white shadow-inner">
    <div class="absolute -top-24 -left-24 w-96 h-96 rounded-full bg-white/15 blur-3xl pointer-events-none"></div>
    <div class="absolute -bottom-24 -right-24 w-96 h-96 rounded-full bg-emerald-300/25 blur-3xl pointer-events-none"></div>

    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 lg:gap-12 items-center">
        
        <div class="lg:col-span-7 text-center lg:text-left space-y-6">
          <span class="font-sans inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-white/20 backdrop-blur-md text-white text-xs font-bold uppercase tracking-wider shadow-sm">
            Explore 120+ Cities
          </span>
          
          <h2 class="font-heading text-3xl sm:text-5xl font-black tracking-tight leading-tight text-white">
            Find your local guide, unlock authentic moments.
          </h2>
          
          <p class="font-sans text-emerald-50 text-base sm:text-lg max-w-2xl mx-auto lg:mx-0 font-normal leading-relaxed">
            Skip generic tour buses. Connect directly with verified local experts for private, fully customizable city walks and culinary adventures.
          </p>

          <form @submit.prevent="handleSearch" class="mt-8 flex flex-col sm:flex-row items-center gap-2.5 bg-white p-2 rounded-2xl sm:rounded-full shadow-2xl max-w-xl mx-auto lg:mx-0">
            <div class="flex items-center gap-3 px-4 py-2.5 w-full text-zinc-800">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-5 h-5 text-emerald-600 shrink-0">
                <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
              </svg>
              <input 
                v-model="searchQuery" 
                type="text" 
                placeholder="Where are you traveling to next?" 
                class="font-sans w-full bg-transparent text-sm sm:text-base text-zinc-900 placeholder-zinc-400 focus:outline-none font-medium"
              />
            </div>
            <button 
              type="submit" 
              class="font-heading w-full sm:w-auto px-8 py-3.5 bg-zinc-900 hover:bg-zinc-800 text-white font-bold text-sm rounded-xl sm:rounded-full transition-all duration-200 active:scale-95 shrink-0 shadow-md cursor-pointer"
            >
              Search
            </button>
          </form>

          <div class="font-sans pt-4 flex flex-wrap items-center justify-center lg:justify-start gap-6 text-xs sm:text-sm font-semibold text-emerald-100">
            <span class="flex items-center gap-1.5">
              <svg class="w-4 h-4 text-emerald-200" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/></svg>
              Verified Local Hosts
            </span>
            <span class="flex items-center gap-1.5">
              <svg class="w-4 h-4 text-emerald-200" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/></svg>
              Flexible Cancellation
            </span>
            <span class="flex items-center gap-1.5">
              <svg class="w-4 h-4 text-emerald-200" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/></svg>
              100% Private Tours
            </span>
          </div>
        </div>

        <div class="lg:col-span-5">
          <div class="bg-white/10 backdrop-blur-md border border-white/20 rounded-3xl p-6 sm:p-8 text-white shadow-xl space-y-5 hover:border-white/40 transition-all duration-300">
            <div class="font-sans inline-block px-3 py-1 rounded-full bg-emerald-400/20 border border-emerald-300/30 text-emerald-100 text-xs font-bold uppercase tracking-wider">
              Become a Guide
            </div>
            
            <h3 class="font-heading text-2xl font-black leading-snug">
              Love your city? Share it and earn on your schedule.
            </h3>
            
            <p class="font-sans text-xs sm:text-sm text-emerald-100 leading-relaxed font-normal">
              Join thousands of local historians, foodies, and creators hosting tours on Leeto. Set your own prices and host on your terms.
            </p>

            <div class="pt-2">
              <a 
                href="#host-signup" 
                class="font-heading block text-center w-full py-3.5 px-6 bg-white hover:bg-emerald-50 text-emerald-950 font-bold text-sm rounded-xl transition-all duration-200 shadow-md hover:shadow-lg active:scale-95 cursor-pointer"
              >
                Apply to Become a Host →
              </a>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>