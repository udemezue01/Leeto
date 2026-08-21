<script setup>
import { ref } from 'vue'

// Reactive filter state
const selectedContinent = ref('')
const searchDestination = ref('')
const selectedCategory = ref('')
const maxPrice = ref(200)
const selectedDuration = ref('any')
const verifiedOnly = ref(true)
const privateOnly = ref(false)
const instantBook = ref(false)
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen">
    
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">

      <!-- =============================================================== -->
      <!-- SECTION HEADER                                                  -->
      <!-- =============================================================== -->
      <div class="flex flex-col md:flex-row md:items-end justify-between mb-8 gap-4 border-b border-zinc-200/80 pb-6">
        <div>
          <!-- Badge Indicator -->
          <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider mb-3">
            <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
            Verified Local Experts Worldwide
          </div>
          <h1 class="font-heading text-3xl sm:text-4xl font-black text-zinc-900 tracking-tight">
            Explore Experiences by <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">Local Guides</span>
          </h1>
          <p class="font-sans text-zinc-600 mt-1.5 text-sm sm:text-base font-medium">Discover private tours, authentic food walks, and hidden city spots tailored around your itinerary.</p>
        </div>

        <!-- Quick Metrics Summary -->
        <div class="flex items-center gap-4 text-xs font-semibold text-zinc-600 bg-white px-4 py-3 rounded-2xl border border-zinc-200/80 shadow-sm shrink-0 font-sans">
          <div class="flex items-center gap-2">
            <span class="flex h-2 w-2 rounded-full bg-emerald-500"></span>
            <span>240+ Guides Active Now</span>
          </div>
          <span class="text-zinc-300">|</span>
          <div class="flex items-center gap-1">
            <span class="text-amber-500 font-bold">★ 4.98</span>
            <span class="text-zinc-500 font-medium">(12.4k Reviews)</span>
          </div>
        </div>
      </div>

      <!-- =============================================================== -->
      <!-- MAIN PAGE LAYOUT: SPLIT INTO 3 PARTS                           -->
      <!-- Part 1: Filter Sidebar (1 Col) | Parts 2 & 3: Experience Grid  -->
      <!-- =============================================================== -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">

        <!-- ============================================================= -->
        <!-- PART 1: FILTER SIDEBAR FORM (1 / 3 Columns on Desktop)        -->
        <!-- Sticky on desktop for seamless browsing                        -->
        <!-- ============================================================= -->
        <aside class="lg:col-span-1">
          <div class="bg-white rounded-3xl border border-zinc-200/80 shadow-xl shadow-zinc-200/50 p-6 lg:sticky lg:top-8 space-y-6">
            
            <!-- Filter Header -->
            <div class="flex items-center justify-between border-b border-zinc-100 pb-4">
              <div class="flex items-center gap-2.5">
                <div class="w-8 h-8 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 6h9.75M10.5 6a1.5 1.5 0 1 1-3 0m3 0a1.5 1.5 0 1 0-3 0M3.75 6H7.5m3 12h9.75m-9.75 0a1.5 1.5 0 1 1-3 0m3 0a1.5 1.5 0 1 0-3 0m-3.75 0H7.5m9-6h3.75m-3.75 0a1.5 1.5 0 1 1-3 0m3 0a1.5 1.5 0 1 0-3 0M3.75 12h7.5" />
                  </svg>
                </div>
                <h3 class="font-heading font-bold text-zinc-900 text-base">Filter Guides</h3>
              </div>
              <button @click="selectedContinent = ''; searchDestination = ''; selectedCategory = ''; maxPrice = 200;" class="text-xs text-emerald-600 hover:text-emerald-800 font-bold transition-colors font-sans">Reset All</button>
            </div>

            <!-- Form Fields -->
            <form @submit.prevent class="space-y-5 font-sans">
              
              <!-- 1. Continent Selector -->
              <div>
                <label class="block text-xs font-bold text-zinc-700 uppercase tracking-wider mb-2">Continent / Region</label>
                <select v-model="selectedContinent" class="w-full px-3.5 py-2.5 text-sm bg-stone-50 border border-zinc-200/70 rounded-xl focus:outline-none focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 font-semibold text-zinc-800 transition-all cursor-pointer">
                  <option value="">All Continents</option>
                  <option value="asia">Asia</option>
                  <option value="europe">Europe</option>
                  <option value="africa">Africa</option>
                  <option value="north-america">North America</option>
                  <option value="south-america">South America</option>
                  <option value="oceania">Oceania & Pacific</option>
                </select>
              </div>

              <!-- 2. City / Destination Search -->
              <div>
                <label class="block text-xs font-bold text-zinc-700 uppercase tracking-wider mb-2">City or Country</label>
                <div class="relative">
                  <input 
                    v-model="searchDestination"
                    type="text" 
                    placeholder="Search e.g. Kyoto, Rome, Lisbon..." 
                    class="w-full pl-10 pr-4 py-2.5 text-sm bg-stone-50 border border-zinc-200/70 rounded-xl focus:outline-none focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 font-semibold text-zinc-900 placeholder-zinc-400 transition-all"
                  />
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4 text-emerald-600 absolute left-3.5 top-3">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                    <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
                  </svg>
                </div>
              </div>

              <!-- 3. Category Selector -->
              <div>
                <label class="block text-xs font-bold text-zinc-700 uppercase tracking-wider mb-2">Experience Category</label>
                <select v-model="selectedCategory" class="w-full px-3.5 py-2.5 text-sm bg-stone-50 border border-zinc-200/70 rounded-xl focus:outline-none focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 font-semibold text-zinc-800 transition-all cursor-pointer">
                  <option value="">All Categories</option>
                  <option value="food">Food & Drinks</option>
                  <option value="history">History & Walking</option>
                  <option value="adventure">Adventure & Outdoor</option>
                  <option value="nightlife">Nightlife & Local Secrets</option>
                  <option value="art">Art, Photo & Architecture</option>
                </select>
              </div>

              <!-- 4. Max Rate Range -->
              <div>
                <div class="flex justify-between items-center mb-2">
                  <label class="text-xs font-bold text-zinc-700 uppercase tracking-wider">Max Rate / Person</label>
                  <span class="text-xs font-bold text-emerald-600">${{ maxPrice }} USD</span>
                </div>
                <input 
                  type="range" 
                  min="25" 
                  max="300" 
                  step="5" 
                  v-model="maxPrice" 
                  class="w-full accent-emerald-600 cursor-pointer" 
                />
                <div class="flex justify-between text-[11px] text-zinc-400 font-medium mt-1">
                  <span>$25</span>
                  <span>$300+</span>
                </div>
              </div>

              <!-- 5. Tour Duration -->
              <div>
                <label class="block text-xs font-bold text-zinc-700 uppercase tracking-wider mb-2">Tour Duration</label>
                <select v-model="selectedDuration" class="w-full px-3.5 py-2.5 text-sm bg-stone-50 border border-zinc-200/70 rounded-xl focus:outline-none focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 font-semibold text-zinc-800 transition-all cursor-pointer">
                  <option value="any">Any Duration</option>
                  <option value="short">Short Walk (1 - 2 Hours)</option>
                  <option value="half-day">Half Day (3 - 5 Hours)</option>
                  <option value="full-day">Full Day (6+ Hours)</option>
                </select>
              </div>

              <!-- 6. Verification & Criteria Checkboxes -->
              <div class="space-y-2.5 pt-3 border-t border-zinc-100">
                <label class="block text-xs font-bold text-zinc-700 uppercase tracking-wider mb-2">Verification & Perks</label>
                <label class="flex items-center gap-2.5 text-xs sm:text-sm font-semibold text-zinc-700 cursor-pointer">
                  <input type="checkbox" v-model="verifiedOnly" class="w-4 h-4 rounded text-emerald-600 focus:ring-emerald-600 border-zinc-300 accent-emerald-600" />
                  <span>100% Background Checked</span>
                </label>
                <label class="flex items-center gap-2.5 text-xs sm:text-sm font-semibold text-zinc-700 cursor-pointer">
                  <input type="checkbox" v-model="privateOnly" class="w-4 h-4 rounded text-emerald-600 focus:ring-emerald-600 border-zinc-300 accent-emerald-600" />
                  <span>Private Tours Only</span>
                </label>
                <label class="flex items-center gap-2.5 text-xs sm:text-sm font-semibold text-zinc-700 cursor-pointer">
                  <input type="checkbox" v-model="instantBook" class="w-4 h-4 rounded text-emerald-600 focus:ring-emerald-600 border-zinc-300 accent-emerald-600" />
                  <span>Instant Confirmation</span>
                </label>
              </div>

              <!-- Filter Apply Button -->
              <button type="button" class="w-full py-3 px-4 bg-zinc-900 hover:bg-emerald-600 text-white text-sm font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200 shadow-md">
                <span>Apply Filters</span>
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
                </svg>
              </button>
            </form>
          </div>
        </aside>

        <!-- ============================================================= -->
        <!-- PART 2 & 3: EXPERIENCES GRID (2 / 3 Columns on Desktop)      -->
        <!-- Displaying 12 Verified Local Experiences                      -->
        <!-- ============================================================= -->
        <main class="lg:col-span-2 space-y-8 font-sans">
          
          <!-- Sorting & Results Controls -->
          <div class="flex items-center justify-between bg-white px-5 py-3.5 rounded-2xl border border-zinc-200/80 shadow-sm text-sm">
            <p class="text-zinc-600 font-medium">Showing <span class="font-bold text-zinc-900">1 - 12</span> of <span class="font-bold text-zinc-900">240+</span> experiences</p>
            <div class="flex items-center gap-2">
              <span class="text-zinc-400 text-xs font-semibold hidden sm:inline">Sort by:</span>
              <select class="bg-stone-50 border border-zinc-200/80 text-xs font-bold text-zinc-800 rounded-xl px-3 py-2 focus:outline-none focus:ring-1 focus:ring-emerald-600 cursor-pointer">
                <option>Highest Rated</option>
                <option>Most Popular</option>
                <option>Price: Low to High</option>
                <option>Price: High to Low</option>
              </select>
            </div>
          </div>

          <!-- 12-EXPERIENCE GRID CONTAINER -->
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">

            <!-- CARD 1: CAPE TOWN -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-amber-500 text-white font-heading font-black text-xs flex items-center justify-center">TN</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Thabo Ndlovu</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Cape Town, SA</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Bo-Kaap Culinary & Secret Sunset Ridge Walk</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Taste traditional Cape Malay dishes, explore vibrant colorful streets, and view Table Mountain at twilight.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$65 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.99 <span class="text-zinc-400 font-normal text-xs">(142)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 2: KYOTO -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-emerald-700 text-white font-heading font-black text-xs flex items-center justify-center">KS</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Kenji Sato</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Kyoto, Japan</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Hidden Bamboo Groves & Private Tea Ceremony</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Bypass crowds to visit a 300-year-old family tea master and secret Arashiyama sanctuaries.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$95 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 5.00 <span class="text-zinc-400 font-normal text-xs">(210)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 3: ROME -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-rose-600 text-white font-heading font-black text-xs flex items-center justify-center">GR</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Giulia Rossi</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Rome, Italy</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Trastevere Street Food & Ancient Wine Cellars</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Indulge in artisanal gelato, hand-rolled pasta, and historic underground cellars away from tourist traps.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$80 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.97 <span class="text-zinc-400 font-normal text-xs">(189)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 4: LISBON -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-amber-600 text-white font-heading font-black text-xs flex items-center justify-center">TS</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Tiago Silva</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Lisbon, Portugal</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Alfama Fado Alleyways & Scenic Viewpoint Photography</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Walk through medieval neighborhoods, capture breathtaking views, and enjoy authentic pastel de nata.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$55 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.96 <span class="text-zinc-400 font-normal text-xs">(98)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 5: BALI -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-teal-600 text-white font-heading font-black text-xs flex items-center justify-center">WS</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Wayan Sudira</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Bali, Indonesia</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Ubud Hidden Waterfalls & Organic Jungle Cooking</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Swim in untouched jungle cascades and prepare traditional Balinese meals with fresh farm ingredients.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$45 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.98 <span class="text-zinc-400 font-normal text-xs">(312)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 6: HANOI -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-violet-600 text-white font-heading font-black text-xs flex items-center justify-center">LN</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Linh Nguyen</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Hanoi, Vietnam</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Old Quarter Midnight Market & Egg Coffee Workshop</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Navigate labyrinth alleyways, sip authentic egg coffee, and sample legendary street stalls.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$35 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.99 <span class="text-zinc-400 font-normal text-xs">(175)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 7: MEXICO CITY -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-orange-600 text-white font-heading font-black text-xs flex items-center justify-center">MH</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Mateo Hernandez</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Mexico City, MX</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Coyoacán Artisan Markets & Mezcal Tasting</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Uncover bohemian art history, visit traditional markets, and learn craft mezcal distillation.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$60 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.95 <span class="text-zinc-400 font-normal text-xs">(88)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 8: PARIS -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-blue-700 text-white font-heading font-black text-xs flex items-center justify-center">CL</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Camille Laurent</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Paris, France</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Montmartre Artists & Secret Bakery Crawl</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Explore hidden bohemian studios and savor award-winning croissants with a local art historian.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$85 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.98 <span class="text-zinc-400 font-normal text-xs">(164)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 9: BUENOS AIRES -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-indigo-600 text-white font-heading font-black text-xs flex items-center justify-center">SM</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Sofia Morales</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Buenos Aires, AR</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">San Telmo Underground Tango & Malbec Tasting</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Experience secret neighbourhood tango halls (milongas) and classic Argentinian steaks.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$50 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.97 <span class="text-zinc-400 font-normal text-xs">(102)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 10: CAIRO -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-amber-700 text-white font-heading font-black text-xs flex items-center justify-center">TM</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Tariq Mansour</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Cairo, Egypt</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Islamic Cairo Bazaar & Rooftop Citadel Sunset</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Walk Khan el-Khalili spice markets with an Egyptologist and enjoy tea overlooking the skyline.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$40 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.96 <span class="text-zinc-400 font-normal text-xs">(128)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 11: SYDNEY -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-cyan-700 text-white font-heading font-black text-xs flex items-center justify-center">CB</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Chloe Bennett</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">Sydney, Australia</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Northern Beaches Secret Coastal Hike & Native Wildlife</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Discover hidden tidal pools, secluded surf beaches, and native bushland walks.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$75 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.99 <span class="text-zinc-400 font-normal text-xs">(91)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

            <!-- CARD 12: NEW YORK -->
            <div class="bg-white rounded-2xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 p-6 flex flex-col justify-between group">
              <div>
                <div class="flex items-center justify-between mb-4">
                  <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-purple-700 text-white font-heading font-black text-xs flex items-center justify-center">MK</div>
                    <div>
                      <h4 class="font-heading text-xs font-bold text-zinc-900">Marcus King</h4>
                      <div class="flex items-center gap-1 text-[11px] text-emerald-600 font-bold">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-3.5 h-3.5"><path fill-rule="evenodd" d="M10 18a8 8 0 1 0 0-16 8 8 0 0 0 0 16Zm3.857-9.809a.75.75 0 0 0-1.214-.882l-3.483 4.79-1.88-1.88a.75.75 0 1 0-1.06 1.061l2.5 2.5a.75.75 0 0 0 1.137-.089l4-5.5Z" clip-rule="evenodd" /></svg>
                        Verified Local
                      </div>
                    </div>
                  </div>
                  <span class="px-2.5 py-1 text-[11px] font-bold bg-stone-100 text-zinc-700 rounded-lg">New York, USA</span>
                </div>
                <h3 class="font-heading text-lg font-extrabold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors line-clamp-2">Brooklyn Street Art & Underground Jazz Speakeasies</h3>
                <p class="text-xs text-zinc-500 font-medium line-clamp-2 mb-4">Tour Bushwick mural alleys followed by password-only live jazz clubs in Greenwich Village.</p>
              </div>
              <div>
                <div class="grid grid-cols-2 gap-3 py-3 px-4 bg-stone-50 rounded-xl mb-5 border border-zinc-100">
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rate</p><p class="text-sm font-black text-zinc-900">$90 / person</p></div>
                  <div><p class="text-[10px] uppercase tracking-wider text-zinc-400 font-bold">Rating</p><p class="text-sm font-black text-amber-500">★ 4.98 <span class="text-zinc-400 font-normal text-xs">(215)</span></p></div>
                </div>
                <button class="w-full py-3 px-4 bg-zinc-900 group-hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200">
                  <span>View Details</span>
                  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-4 h-4"><path fill-rule="evenodd" d="M3 10a.75.75 0 0 1 .75-.75h10.638L10.23 5.29a.75.75 0 1 1 1.04-1.08l5.5 5.25a.75.75 0 0 1 0 1.08l-5.5 5.25a.75.75 0 1 1-1.04-1.08l4.158-3.96H3.75A.75.75 0 0 1 3 10Z" clip-rule="evenodd" /></svg>
                </button>
              </div>
            </div>

          </div>

          <!-- ============================================================= -->
          <!-- PAGINATION CONTROLS SECTION                                   -->
          <!-- Accessible, Leeto-styled pagination controls                 -->
          <!-- ============================================================= -->
          <div class="flex items-center justify-between border-t border-zinc-200/80 pt-6 mt-8 font-sans">
            
            <!-- Mobile / Standard Prev Button -->
            <button class="inline-flex items-center gap-2 px-4 py-2 text-xs font-bold text-zinc-700 bg-white border border-zinc-200/80 rounded-xl hover:bg-stone-100 transition duration-150 shadow-sm disabled:opacity-50" disabled>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5 8.25 12l7.5-7.5" />
              </svg>
              <span>Previous</span>
            </button>

            <!-- Page Number Buttons (Desktop & Tablet) -->
            <div class="hidden sm:flex items-center gap-1.5">
              <button class="w-10 h-10 rounded-xl text-xs font-bold bg-zinc-900 text-white shadow-md flex items-center justify-center">1</button>
              <button class="w-10 h-10 rounded-xl text-xs font-bold text-zinc-600 hover:bg-white border border-transparent hover:border-zinc-200 flex items-center justify-center transition">2</button>
              <button class="w-10 h-10 rounded-xl text-xs font-bold text-zinc-600 hover:bg-white border border-transparent hover:border-zinc-200 flex items-center justify-center transition">3</button>
              <span class="px-1 text-zinc-400 font-bold">...</span>
              <button class="w-10 h-10 rounded-xl text-xs font-bold text-zinc-600 hover:bg-white border border-transparent hover:border-zinc-200 flex items-center justify-center transition">20</button>
            </div>

            <!-- Mobile / Standard Next Button -->
            <button class="inline-flex items-center gap-2 px-4 py-2 text-xs font-bold text-white bg-zinc-900 hover:bg-emerald-600 rounded-xl transition duration-150 shadow-md">
              <span>Next</span>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                <path stroke-linecap="round" stroke-linejoin="round" d="m8.25 4.5 7.5 7.5-7.5 7.5" />
              </svg>
            </button>

          </div>

        </main>
      </div>

    </div>
  </section>
</template>