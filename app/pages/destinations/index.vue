<script setup>
import { ref, computed } from 'vue'

const activeContinent = ref('all')
const searchQuery = ref('')

const continents = [
  { id: 'all', label: 'All Continents' },
  { id: 'asia', label: 'Asia' },
  { id: 'europe', label: 'Europe' },
  { id: 'africa', label: 'Africa' },
  { id: 'americas', label: 'Americas' },
  { id: 'oceania', label: 'Oceania' }
]

const destinations = [
  {
    id: 1,
    city: 'Kyoto',
    country: 'Japan',
    continent: 'asia',
    image: 'https://images.unsplash.com/photo-1493976040374-85c8e12f0c0e?auto=format&fit=crop&w=800&q=80',
    guidesCount: 48,
    rating: 4.99,
    reviews: 320,
    tags: ['Tea Ceremonies', 'Temples', 'Bamboo Groves'],
    featured: true
  },
  {
    id: 2,
    city: 'Rome',
    country: 'Italy',
    continent: 'europe',
    image: 'https://images.unsplash.com/photo-1552832230-c0197dd311b5?auto=format&fit=crop&w=800&q=80',
    guidesCount: 62,
    rating: 4.97,
    reviews: 410,
    tags: ['Street Food', 'Ancient History', 'Wine Walks'],
    featured: true
  },
  {
    id: 3,
    city: 'Cape Town',
    country: 'South Africa',
    continent: 'africa',
    image: 'https://images.unsplash.com/photo-1580618672591-eb180b1a973f?auto=format&fit=crop&w=800&q=80',
    guidesCount: 35,
    rating: 4.98,
    reviews: 215,
    tags: ['Table Mountain', 'Bo-Kaap Food', 'Coastal Hikes'],
    featured: true
  },
  {
    id: 4,
    city: 'Lisbon',
    country: 'Portugal',
    continent: 'europe',
    image: 'https://images.unsplash.com/photo-1509839862600-1bc96d162d34?auto=format&fit=crop&w=800&q=80',
    guidesCount: 41,
    rating: 4.96,
    reviews: 180,
    tags: ['Fado Music', 'Viewpoints', 'Pastel de Nata'],
    featured: false
  },
  {
    id: 5,
    city: 'Bali',
    country: 'Indonesia',
    continent: 'asia',
    image: 'https://images.unsplash.com/photo-1537996194471-e657df975ab4?auto=format&fit=crop&w=800&q=80',
    guidesCount: 54,
    rating: 4.98,
    reviews: 290,
    tags: ['Jungle Waterfalls', 'Organic Cooking', 'Rice Terraces'],
    featured: true
  },
  {
    id: 6,
    city: 'Mexico City',
    country: 'Mexico',
    continent: 'americas',
    image: 'https://images.unsplash.com/photo-1518638150340-f706e86654de?auto=format&fit=crop&w=800&q=80',
    guidesCount: 39,
    rating: 4.95,
    reviews: 160,
    tags: ['Taco Crawls', 'Art Markets', 'Mezcal Tasting'],
    featured: false
  },
  {
    id: 7,
    city: 'Ha Long Bay',
    country: 'Vietnam',
    continent: 'asia',
    image: 'https://images.unsplash.com/photo-1528127269322-539801943592?auto=format&fit=crop&w=800&q=80',
    guidesCount: 29,
    rating: 4.98,
    reviews: 240,
    tags: ['Private Cruises', 'Cave Kayaking', 'Floating Villages'],
    featured: false
  },
  {
    id: 8,
    city: 'Cairo',
    country: 'Egypt',
    continent: 'africa',
    image: 'https://images.unsplash.com/photo-1572252821143-035a2283e7ee?auto=format&fit=crop&w=800&q=80',
    guidesCount: 31,
    rating: 4.94,
    reviews: 145,
    tags: ['Egyptologists', 'Spice Bazaars', 'Citadel Sunset'],
    featured: false
  },
  {
    id: 9,
    city: 'Sydney',
    country: 'Australia',
    continent: 'oceania',
    image: 'https://images.unsplash.com/photo-1506973035872-a4ec16b8e8d9?auto=format&fit=crop&w=800&q=80',
    guidesCount: 27,
    rating: 4.99,
    reviews: 110,
    tags: ['Coastal Walks', 'Harbor Kayaking', 'Native Wildlife'],
    featured: false
  }
]

const filteredDestinations = computed(() => {
  return destinations.filter(dest => {
    const matchesContinent = activeContinent.value === 'all' || dest.continent === activeContinent.value
    const matchesSearch = dest.city.toLowerCase().includes(searchQuery.value.toLowerCase()) || 
                          dest.country.toLowerCase().includes(searchQuery.value.toLowerCase())
    return matchesContinent && matchesSearch
  })
})
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen">
    
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-12">

      <!-- Section Header -->
      <div class="text-center max-w-3xl mx-auto space-y-6">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
          Global Destination Hub
        </div>

        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
          Explore cities across <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">every continent.</span>
        </h1>

        <p class="text-base sm:text-lg text-zinc-600 font-medium leading-relaxed">
          From ancient alleyways in Kyoto to coastal trails in Cape Town, discover authentic private tours hosted by verified local experts worldwide.
        </p>

        <!-- Search input box -->
        <div class="max-w-md mx-auto relative">
          <input 
            v-model="searchQuery"
            type="text" 
            placeholder="Search city or country (e.g. Japan, Rome)..." 
            class="w-full pl-11 pr-4 py-3 bg-white text-zinc-900 placeholder-zinc-400 text-sm font-semibold rounded-2xl shadow-md border border-zinc-200/80 focus:outline-none focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 transition-all"
          />
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5 text-emerald-600 absolute left-3.5 top-3.5">
            <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
            <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
          </svg>
        </div>
      </div>

      <!-- Continent Navigation Tabs -->
      <div class="flex items-center justify-center flex-wrap gap-2 pt-2">
        <button
          v-for="continent in continents"
          :key="continent.id"
          @click="activeContinent = continent.id"
          :class="[
            'px-5 py-2.5 rounded-xl font-bold text-xs uppercase tracking-wider transition-all duration-200',
            activeContinent === continent.id
              ? 'bg-zinc-900 text-white shadow-md'
              : 'bg-white text-zinc-600 border border-zinc-200/80 hover:border-emerald-600 hover:text-emerald-600'
          ]"
        >
          {{ continent.label }}
        </button>
      </div>

      <!-- Destinations Card Grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="dest in filteredDestinations"
          :key="dest.id"
          class="bg-white rounded-3xl border border-zinc-200/80 shadow-lg shadow-zinc-200/50 overflow-hidden flex flex-col justify-between group hover:-translate-y-1 transition-all duration-300"
        >
          <div>
            <!-- Image Header -->
            <div class="relative h-60 w-full overflow-hidden bg-zinc-900">
              <img 
                :src="dest.image" 
                :alt="dest.city" 
                class="w-full h-full object-cover opacity-90 group-hover:scale-105 transition-transform duration-500"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-zinc-900/80 via-transparent to-transparent"></div>
              
              <!-- Badges Overlay -->
              <div class="absolute top-4 left-4 flex items-center gap-2">
                <span class="bg-zinc-900/80 backdrop-blur-md px-3 py-1 rounded-full text-amber-400 text-[11px] font-bold uppercase tracking-wider border border-white/10">
                  {{ dest.continent }}
                </span>
                <span v-if="dest.featured" class="bg-emerald-600/90 backdrop-blur-md px-3 py-1 rounded-full text-white text-[11px] font-bold uppercase tracking-wider">
                  Featured
                </span>
              </div>

              <!-- City & Country Overlay -->
              <div class="absolute bottom-4 left-4 right-4 text-white">
                <h3 class="text-2xl font-black leading-tight">{{ dest.city }}</h3>
                <p class="text-xs font-semibold text-stone-200">{{ dest.country }}</p>
              </div>
            </div>

            <!-- Card Content Body -->
            <div class="p-6 space-y-4">
              <div class="flex items-center justify-between text-xs font-bold text-zinc-600 border-b border-zinc-100 pb-3">
                <span class="flex items-center gap-1 text-emerald-700">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.501 20.118a7.5 7.5 0 0114.998 0A17.933 17.933 0 0112 21.75c-2.676 0-5.216-.584-7.499-1.632z" />
                  </svg>
                  {{ dest.guidesCount }} Active Local Guides
                </span>
                <span class="text-amber-500">
                  ★ {{ dest.rating }} <span class="text-zinc-400 font-normal">({{ dest.reviews }})</span>
                </span>
              </div>

              <!-- Popular Tags -->
              <div>
                <p class="text-[11px] font-bold uppercase tracking-wider text-zinc-400 mb-2">Top Experiences:</p>
                <div class="flex flex-wrap gap-1.5">
                  <span 
                    v-for="tag in dest.tags" 
                    :key="tag" 
                    class="px-2.5 py-1 rounded-lg bg-stone-100 text-zinc-700 text-xs font-semibold"
                  >
                    {{ tag }}
                  </span>
                </div>
              </div>
            </div>
          </div>

          <!-- Card Footer Button -->
          <div class="p-6 pt-0">
            <button class="w-full py-3 bg-zinc-900 group-hover:bg-emerald-600 text-white font-bold text-xs rounded-xl shadow-md transition-all duration-200 flex items-center justify-center gap-2">
              <span>Explore {{ dest.city }} Guides</span>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4">
                <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
              </svg>
            </button>
          </div>
        </div>
      </div>

      <!-- Empty State -->
      <div v-if="filteredDestinations.length === 0" class="text-center py-16 bg-white rounded-3xl border border-zinc-200/80 shadow-sm">
        <p class="text-lg font-bold text-zinc-800">No destinations match your search.</p>
        <p class="text-sm text-zinc-500 mt-1">Try resetting your continent filter or typing a different city.</p>
        <button @click="activeContinent = 'all'; searchQuery = ''" class="mt-4 px-6 py-2.5 bg-zinc-900 text-white font-bold text-xs rounded-xl">
          Reset All Filters
        </button>
      </div>

      <!-- Request Custom City Banner -->
      <div class="bg-zinc-900 rounded-3xl p-8 sm:p-12 text-white relative overflow-hidden shadow-2xl border border-zinc-800 flex flex-col md:flex-row items-center justify-between gap-8">
        <div class="absolute top-0 right-0 -mt-10 -mr-10 w-80 h-80 bg-emerald-500/20 rounded-full blur-3xl pointer-events-none"></div>
        
        <div class="space-y-3 text-center md:text-left max-w-xl relative z-10">
          <span class="inline-block px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold uppercase tracking-wider border border-emerald-500/30">
            Don't see your next stop?
          </span>
          <h2 class="text-2xl sm:text-3xl font-black text-white tracking-tight">
            Request a verified guide in any city worldwide.
          </h2>
          <p class="text-stone-300 font-medium text-xs sm:text-sm leading-relaxed">
            We onboard vetted local experts in 50+ new destinations every month. Tell us where you are traveling next!
          </p>
        </div>

        <button class="w-full sm:w-auto px-8 py-4 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-sm rounded-xl shadow-lg transition-all duration-200 shrink-0 relative z-10">
          Request a Destination
        </button>
      </div>

    </div>
  </section>
</template>