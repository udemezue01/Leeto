<script setup>
import { ref } from 'vue'

const carouselRef = ref(null)

const tours = ref([
  {
    id: 1,
    title: 'Tokyo After Dark: Shinjuku Food & Alleyway Crawl',
    location: 'Tokyo, Japan',
    image: 'https://images.unsplash.com/photo-1503899036084-c55cdd92da26?auto=format&fit=crop&w=800&q=80',
    category: 'Food & Nightlife',
    rating: 4.98,
    reviewsCount: 142,
    duration: '3.5 hrs',
    price: 75,
    guide: {
      name: 'Kenji S.',
      avatar: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&w=120&q=80',
      verified: true
    }
  },
  {
    id: 2,
    title: 'Secret Temples & Street Food of Hidden Bangkok',
    location: 'Bangkok, Thailand',
    image: 'https://images.unsplash.com/photo-1508009603885-50cf7c579365?auto=format&fit=crop&w=800&q=80',
    category: 'Culture & Heritage',
    rating: 4.95,
    reviewsCount: 98,
    duration: '4 hrs',
    price: 48,
    guide: {
      name: 'Mali T.',
      avatar: 'https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=120&q=80',
      verified: true
    }
  },
  {
    id: 3,
    title: 'Oaxaca to Bali: Sacred Waterfalls & Jungle Trekking',
    location: 'Ubud, Indonesia',
    image: 'https://images.unsplash.com/photo-1537996194471-e657df975ab4?auto=format&fit=crop&w=800&q=80',
    category: 'Nature & Adventure',
    rating: 4.92,
    reviewsCount: 210,
    duration: '6 hrs',
    price: 60,
    guide: {
      name: 'Wayan K.',
      avatar: 'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?auto=format&fit=crop&w=120&q=80',
      verified: true
    }
  },
  {
    id: 4,
    title: 'Old Seoul Night Market & Hidden Pub Hopping',
    location: 'Seoul, South Korea',
    image: 'https://images.unsplash.com/photo-1538485399081-7191377e8241?auto=format&fit=crop&w=800&q=80',
    category: 'Nightlife',
    rating: 4.97,
    reviewsCount: 86,
    duration: '3 hrs',
    price: 55,
    guide: {
      name: 'Min-ho L.',
      avatar: 'https://images.unsplash.com/photo-1522075469751-3a6694fb2f61?auto=format&fit=crop&w=120&q=80',
      verified: true
    }
  },
  {
    id: 5,
    title: 'Hanoi Street Food Walking Tour with Local Chef',
    location: 'Hanoi, Vietnam',
    image: 'https://images.unsplash.com/photo-1528127269322-539801943592?auto=format&fit=crop&w=800&q=80',
    category: 'Culinary',
    rating: 4.99,
    reviewsCount: 312,
    duration: '3 hrs',
    price: 35,
    guide: {
      name: 'Linh N.',
      avatar: 'https://images.unsplash.com/photo-1544005313-94ddf0286df2?auto=format&fit=crop&w=120&q=80',
      verified: true
    }
  }
])

const scroll = (direction) => {
  if (!carouselRef.value) return
  const scrollAmount = direction === 'left' ? -380 : 380
  carouselRef.value.scrollBy({ left: scrollAmount, behavior: 'smooth' })
}
</script>

<template>
  <section class="bg-stone-50 py-16 sm:py-24 text-zinc-800 font-sans border-t border-zinc-200/80">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- Section Header with Title & Navigation Controls -->
      <div class="flex flex-col sm:flex-row sm:items-end justify-between mb-8 gap-4">
        <div>
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-emerald-100/80 border border-emerald-200/60 text-emerald-800 text-xs font-bold uppercase tracking-wider mb-3">
            <span>🌏</span> Top Rated in Asia
          </div>
          <h2 class="text-3xl sm:text-4xl font-black text-zinc-900 tracking-tight">
            Unforgettable Asian Adventures
          </h2>
          <p class="mt-2 text-sm sm:text-base text-zinc-600 max-w-xl">
            Book top-rated local hosts for private street food walks, sacred temple visits, and secret spots.
          </p>
        </div>

        <!-- Desktop & Mobile Controls -->
        <div class="flex items-center gap-2 self-end sm:self-auto">
          <button 
            @click="scroll('left')"
            type="button"
            class="p-3 rounded-full bg-white border border-zinc-200/80 text-zinc-700 hover:bg-zinc-900 hover:text-white hover:border-zinc-900 transition-all duration-200 shadow-sm active:scale-95 cursor-pointer"
            aria-label="Scroll left"
          >
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-5 h-5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5" />
            </svg>
          </button>
          <button 
            @click="scroll('right')"
            type="button"
            class="p-3 rounded-full bg-white border border-zinc-200/80 text-zinc-700 hover:bg-zinc-900 hover:text-white hover:border-zinc-900 transition-all duration-200 shadow-sm active:scale-95 cursor-pointer"
            aria-label="Scroll right"
          >
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-5 h-5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
            </svg>
          </button>
        </div>
      </div>

      <!-- Carousel Container -->
      <div 
        ref="carouselRef"
        class="flex gap-6 overflow-x-auto snap-x snap-mandatory scrollbar-none scroll-smooth pb-4 -mx-4 px-4 sm:mx-0 sm:px-0"
        style="scrollbar-width: none; -ms-overflow-style: none;"
      >
        <div 
          v-for="tour in tours" 
          :key="tour.id"
          class="snap-start shrink-0 w-[290px] sm:w-[340px] md:w-[360px] bg-white rounded-2xl border border-zinc-200/80 overflow-hidden shadow-sm hover:shadow-xl hover:shadow-zinc-900/5 hover:border-emerald-500/50 transition-all duration-300 flex flex-col group"
        >
          <!-- Image Wrapper -->
          <div class="relative h-52 w-full overflow-hidden bg-zinc-100">
            <img 
              :src="tour.image" 
              :alt="tour.title"
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
              loading="lazy"
            />
            
            <!-- Category Badge -->
            <span class="absolute top-3 left-3 bg-zinc-900/80 backdrop-blur-md text-white text-[11px] font-semibold px-2.5 py-1 rounded-full">
              {{ tour.category }}
            </span>

            <!-- Rating Badge -->
            <div class="absolute bottom-3 left-3 bg-white/90 backdrop-blur-md px-2.5 py-1 rounded-full flex items-center gap-1 text-xs font-bold text-zinc-900 shadow-sm">
              <span class="text-amber-500">★</span>
              <span>{{ tour.rating }}</span>
              <span class="text-zinc-400 font-normal">({{ tour.reviewsCount }})</span>
            </div>
          </div>

          <!-- Content Body -->
          <div class="p-5 flex-1 flex flex-col justify-between">
            <div>
              <!-- Location & Duration -->
              <div class="flex items-center justify-between text-xs text-zinc-500 font-semibold mb-2">
                <span class="flex items-center gap-1 text-emerald-700">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-3.5 h-3.5">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                    <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
                  </svg>
                  {{ tour.location }}
                </span>
                <span>⏱️ {{ tour.duration }}</span>
              </div>

              <!-- Title -->
              <h3 class="text-base font-bold text-zinc-900 line-clamp-2 leading-snug group-hover:text-emerald-600 transition-colors">
                {{ tour.title }}
              </h3>
            </div>

            <!-- Card Footer: Host & Price -->
            <div class="mt-6 pt-4 border-t border-zinc-100 flex items-center justify-between">
              <!-- Guide Info -->
              <div class="flex items-center gap-2.5">
                <div class="relative">
                  <img 
                    :src="tour.guide.avatar" 
                    :alt="tour.guide.name"
                    class="w-8 h-8 rounded-full object-cover ring-2 ring-emerald-500/30"
                  />
                  <span v-if="tour.guide.verified" class="absolute -bottom-0.5 -right-0.5 w-3 h-3 bg-emerald-600 rounded-full border-2 border-white flex items-center justify-center text-[7px] text-white">✓</span>
                </div>
                <div class="text-xs">
                  <p class="font-bold text-zinc-900 leading-none">{{ tour.guide.name }}</p>
                  <p class="text-[10px] text-zinc-400 font-medium">Local Host</p>
                </div>
              </div>

              <!-- Price Tag -->
              <div class="text-right">
                <p class="text-[10px] uppercase tracking-wider font-bold text-zinc-400">From</p>
                <p class="text-base font-black text-zinc-900">${{ tour.price }} <span class="text-xs font-normal text-zinc-500">/ person</span></p>
              </div>
            </div>

          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
/* Utility to hide horizontal scrollbars while keeping swipe scroll functional */
.scrollbar-none::-webkit-scrollbar {
  display: none;
}
</style>