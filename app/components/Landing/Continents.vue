<script setup>
import { ref } from 'vue'

const continents = ref([
  {
    name: 'Africa',
    slug: 'africa',
    guidesCount: '450+ Guides',
    popularSpots: 'Cape Town, Marrakech, Serengeti',
    iconPath: 'M12 3v2.25m6.364.386l-1.591 1.591M21 12h-2.25m-.386 6.364l-1.591-1.591M12 18.75V21m-4.773-4.227l-1.591 1.591M5.25 12H3m4.227-4.773L5.636 5.636M15.75 12a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0z'
  },
  {
    name: 'Asia',
    slug: 'asia',
    guidesCount: '850+ Guides',
    popularSpots: 'Tokyo, Bangkok, Bali',
    iconPath: 'M4.5 19.5l15 0m-13.5-3l12 0m-10.5-3l9 0m-7.5-3l6 0m-4.5-3l3 0m-1.5-3l0 3'
  },
  {
    name: 'Europe',
    slug: 'europe',
    guidesCount: '920+ Guides',
    popularSpots: 'Rome, Paris, Barcelona',
    iconPath: 'M12 21v-8.25M15.75 21v-8.25M8.25 21v-8.25M3 9l9-6 9 6m-1.5 12V10.5M4.5 21V10.5'
  },
  {
    name: 'North America',
    slug: 'north-america',
    guidesCount: '610+ Guides',
    popularSpots: 'New York, Oaxaca, Vancouver',
    iconPath: 'M2.25 21h19.5m-18-18v18m10.5-18v18m6-10.5v10.5m-12-6v6m6-12v12'
  },
  {
    name: 'Oceania',
    slug: 'oceania',
    guidesCount: '340+ Guides',
    popularSpots: 'Sydney, Queenstown, Fiji',
    iconPath: 'M2.25 15a4.5 4.5 0 004.5 4.5H18a3.75 3.75 0 00.41-7.48 5.25 5.25 0 00-10.32-1.33A4.5 4.5 0 002.25 15z'
  },
  {
    name: 'South America',
    slug: 'south-america',
    guidesCount: '480+ Guides',
    popularSpots: 'Cusco, Rio de Janeiro, Buenos Aires',
    iconPath: 'M12 21a9 9 0 100-18 9 9 0 000 18zM12 6v12m-6-6h12'
  }
])
</script>

<template>
  <section class="bg-stone-50 py-16 sm:py-24 text-zinc-800 font-sans border-t border-zinc-200/80">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- Section Header -->
      <div class="flex flex-col md:flex-row md:items-end justify-between mb-12 sm:mb-16 gap-4">
        <div>
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-md bg-emerald-100 text-emerald-800 text-xs font-bold uppercase tracking-wider mb-3">
            Explore Worldwide
          </div>
          <h2 class="font-heading text-3xl sm:text-4xl lg:text-5xl font-black text-zinc-900 tracking-tight">
            Destinations by Continent
          </h2>
          <p class="mt-3 text-zinc-600 text-base sm:text-lg max-w-xl font-sans">
            Find vetted local guides ready to show you hidden gems across all six major regions.
          </p>
        </div>

        <NuxtLink 
          to="/destinations" 
          class="inline-flex items-center gap-2 text-sm font-bold text-zinc-900 hover:text-emerald-600 transition-colors group shrink-0"
        >
          <span>View all destinations</span>
          <svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" class="w-4 h-4 group-hover:translate-x-1 transition-transform" viewBox="0 0 24 24">
            <path d="M5 12h14M12 5l7 7-7 7"></path>
          </svg>
        </NuxtLink>
      </div>

      <!-- Continents Grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 sm:gap-8">
        <NuxtLink 
          v-for="continent in continents" 
          :key="continent.slug"
          :to="`/destinations/${continent.slug}`"
          class="group relative bg-white p-6 sm:p-8 rounded-2xl border border-zinc-200/80 shadow-sm hover:shadow-xl hover:border-emerald-600/50 transition-all duration-300 flex flex-col justify-between"
        >
          <div>
            <!-- Top Bar: Icon & Guide Counter Tag -->
            <div class="flex items-center justify-between mb-6">
              <div class="w-12 h-12 rounded-xl bg-stone-100 group-hover:bg-emerald-600 text-zinc-900 group-hover:text-white flex items-center justify-center transition-colors duration-300 shadow-inner">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.75" stroke="currentColor" class="w-6 h-6">
                  <path stroke-linecap="round" stroke-linejoin="round" :d="continent.iconPath" />
                </svg>
              </div>
              <span class="px-2.5 py-1 rounded-full text-xs font-bold bg-stone-100 text-zinc-700 group-hover:bg-amber-100 group-hover:text-amber-800 transition-colors">
                {{ continent.guidesCount }}
              </span>
            </div>

            <!-- Continent Info -->
            <h3 class="font-heading text-2xl font-black text-zinc-900 group-hover:text-emerald-600 transition-colors tracking-tight">
              {{ continent.name }}
            </h3>
            
            <p class="text-xs text-zinc-500 font-medium mt-2 font-sans">
              <span class="text-zinc-400 uppercase tracking-wider text-[10px] block font-bold">Top Destinations</span>
              {{ continent.popularSpots }}
            </p>
          </div>

          <!-- Bottom Action Link -->
          <div class="mt-8 pt-4 border-t border-zinc-100 flex items-center justify-between text-xs font-bold text-zinc-900 group-hover:text-emerald-600 font-sans">
            <span>Browse {{ continent.name }} guides</span>
            <div class="w-7 h-7 rounded-full bg-stone-50 group-hover:bg-emerald-50 flex items-center justify-center transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-3.5 h-3.5 group-hover:translate-x-0.5 transition-transform">
                <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
              </svg>
            </div>
          </div>
        </NuxtLink>
      </div>

    </div>
  </section>
</template>