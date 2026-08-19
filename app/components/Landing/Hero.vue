<script setup>
import { ref } from 'vue'

const destination = ref('')
const selectedCategory = ref('all')

const popularDestinations = ['Cape Town', 'Kyoto', 'Rome', 'Lisbon', 'Bali']

const handleSearch = () => {
  if (destination.value.trim()) {
    navigateTo({
      path: '/guides',
      query: { destination: destination.value, category: selectedCategory.value }
    })
  }
}
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60">
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-8 items-center">
        
        <!-- Copy & Search Input Widget -->
        <div class="lg:col-span-7 space-y-8 text-center lg:text-left">
          
          <!-- Badge -->
          <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider">
            <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
            Verified Local Experts Worldwide
          </div>

          <!-- Main Heading -->
          <h1 class="text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
            Explore cities like a local, <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">not a tourist.</span>
          </h1>

          <!-- Description -->
          <p class="text-base sm:text-lg text-zinc-600 max-w-2xl mx-auto lg:mx-0 font-medium leading-relaxed">
            Connect with local guides to discover hidden spots, authentic food, and custom tours built around your itinerary.
          </p>

          <!-- Search Widget -->
          <div class="bg-white p-3 sm:p-4 rounded-2xl sm:rounded-3xl shadow-xl shadow-zinc-200/60 border border-zinc-200/80">
            <form @submit.prevent="handleSearch" class="flex flex-col sm:flex-row items-center gap-3">
              
              <!-- Location Field -->
              <div class="relative w-full flex-1 flex items-center px-3 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5 text-emerald-600 shrink-0 mr-2.5">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
                </svg>
                <input 
                  v-model="destination"
                  type="text" 
                  placeholder="Where to? (e.g., Tokyo, Paris)" 
                  class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-semibold focus:outline-none"
                />
              </div>

              <!-- Experience Type Filter -->
              <div class="relative w-full sm:w-48 flex items-center px-3 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5 text-zinc-400 shrink-0 mr-2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M9.568 3H5.25A2.25 2.25 0 003 5.25v4.318c0 .597.237 1.17.659 1.591l9.581 9.581c.699.699 1.78.872 2.607.33a18.095 18.095 0 005.223-5.223c.542-.827.369-1.908-.33-2.607L11.16 3.66A2.25 2.25 0 009.568 3z" />
                </svg>
                <select 
                  v-model="selectedCategory"
                  class="w-full bg-transparent text-zinc-800 text-sm font-semibold focus:outline-none cursor-pointer"
                >
                  <option value="all">All Experiences</option>
                  <option value="food">Food & Drinks</option>
                  <option value="history">History & Walking</option>
                  <option value="adventure">Adventure & Outdoor</option>
                </select>
              </div>

              <!-- Submit Button -->
              <button 
                type="submit" 
                class="w-full sm:w-auto px-6 py-3 bg-zinc-900 hover:bg-emerald-600 text-white font-bold text-sm rounded-xl shadow-md hover:shadow-emerald-600/20 transition-all duration-200 flex items-center justify-center gap-2 shrink-0 group"
              >
                <span>Find Guides</span>
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4 group-hover:translate-x-0.5 transition-transform">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
                </svg>
              </button>

            </form>
          </div>

          <!-- Quick Destination Tags -->
          <div class="flex flex-wrap items-center justify-center lg:justify-start gap-2 text-xs text-zinc-500 font-medium pt-1">
            <span class="font-bold text-zinc-700">Popular:</span>
            <button 
              v-for="city in popularDestinations" 
              :key="city"
              @click="destination = city"
              class="px-2.5 py-1 rounded-lg bg-stone-200/70 hover:bg-zinc-900 hover:text-white transition-colors duration-150"
            >
              {{ city }}
            </button>
          </div>

        </div>

        <!-- Featured Guide Showcase Card -->
        <div class="lg:col-span-5 relative">
          <div class="relative bg-white p-3.5 rounded-3xl shadow-2xl border border-zinc-200/80">
            
            <div class="relative h-80 sm:h-96 rounded-2xl overflow-hidden bg-zinc-900">
              <img 
                src="https://images.unsplash.com/photo-1528127269322-539801943592?auto=format&fit=crop&w=800&q=80" 
                alt="Tour guide showing destination" 
                class="w-full h-full object-cover opacity-90 hover:scale-105 transition-transform duration-500"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-zinc-900/90 via-zinc-900/20 to-transparent"></div>
              
              <!-- Badge Overlay -->
              <div class="absolute top-4 left-4 bg-zinc-900/80 backdrop-blur-md px-3 py-1.5 rounded-full text-white text-xs font-semibold flex items-center gap-2 border border-white/10">
                <span class="relative flex h-2 w-2">
                  <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
                  <span class="relative inline-flex rounded-full h-2 w-2 bg-emerald-500"></span>
                </span>
                Active Guides Nearby
              </div>

              <!-- Destination Footer Overlay -->
              <div class="absolute bottom-4 left-4 right-4 text-white">
                <p class="text-xs uppercase tracking-widest text-amber-400 font-bold">Featured Destination</p>
                <h3 class="text-xl font-bold">Ha Long Bay, Vietnam</h3>
                <div class="flex items-center gap-1.5 mt-1 text-xs text-stone-200">
                  <span class="text-amber-400 font-bold">★ 4.98</span>
                  <span>•</span>
                  <span>240+ Local Experiences</span>
                </div>
              </div>
            </div>

            <!-- Floating Social Proof Badge -->
            <div class="absolute -bottom-5 -left-5 bg-white p-3 rounded-2xl shadow-xl border border-zinc-200/80 hidden sm:flex items-center gap-3">
              <div class="w-10 h-10 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold text-lg">
                🛡️
              </div>
              <div>
                <p class="text-xs font-bold text-zinc-900">100% Verified Guides</p>
                <p class="text-[11px] text-zinc-500">Background checked & reviewed</p>
              </div>
            </div>

          </div>
        </div>

      </div>
    </div>
  </section>
</template>