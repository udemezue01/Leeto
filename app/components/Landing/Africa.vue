<script setup>
import { ref } from 'vue'

const carouselRef = ref(null)

const tours = ref([
  {
    id: 1,
    title: 'Cape Peninsula Coastal Drive & Secret Beach Trail',
    location: 'Cape Town, South Africa',
    image: 'https://images.unsplash.com/photo-1580618672591-eb180b1a973f?auto=format&fit=crop&w=800&q=80',
    category: 'Nature & Coastal',
    rating: 4.99,
    reviewsCount: 184,
    duration: '5 hrs',
    price: 65,
    guide: {
      name: 'Thabo M.',
      avatar: 'https://images.unsplash.com/photo-1531384441138-2736e62e0919?auto=format&fit=crop&w=120&q=80',
      verified: true
    }
  },
  {
    id: 2,
    title: 'Medina Spice Markets & Secret Rooftop Tea Tasting',
    location: 'Marrakech, Morocco',
    image: 'https://images.unsplash.com/photo-1539020140153-e479b8c22e70?auto=format&fit=crop&w=800&q=80',
    category: 'Culture & Food',
    rating: 4.96,
    reviewsCount: 215,
    duration: '3.5 hrs',
    price: 45,
    guide: {
      name: 'Youssef K.',
      avatar: 'https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?auto=format&fit=crop&w=120&q=80',
      verified: true
    }
  },
  {
    id: 3,
    title: 'Maasai-Led Conservation Walk & Bush Safari',
    location: 'Nairobi, Kenya',
    image: 'https://images.unsplash.com/photo-1516426122078-c23e76319801?auto=format&fit=crop&w=800&q=80',
    category: 'Wildlife & Safari',
    rating: 4.98,
    reviewsCount: 162,
    duration: '6 hrs',
    price: 85,
    guide: {
      name: 'David O.',
      avatar: 'https://images.unsplash.com/photo-1522529599102-193c0d76b5b6?auto=format&fit=crop&w=120&q=80',
      verified: true
    }
  },
  {
    id: 4,
    title: 'Stone Town Heritage Walk & Organic Spice Farm Tour',
    location: 'Zanzibar, Tanzania',
    image: 'https://images.unsplash.com/photo-1568322445389-f64ac2515020?auto=format&fit=crop&w=800&q=80',
    category: 'History & Culinary',
    rating: 4.94,
    reviewsCount: 110,
    duration: '4 hrs',
    price: 40,
    guide: {
      name: 'Asha S.',
      avatar: 'https://images.unsplash.com/photo-1531746020798-e6953c6e8e04?auto=format&fit=crop&w=120&q=80',
      verified: true
    }
  },
  {
    id: 5,
    title: 'Afrobeat Lagos Nightlife & Street Food Crawl',
    location: 'Lagos, Nigeria',
    image: 'https://images.unsplash.com/photo-1572252821143-02422791851b?auto=format&fit=crop&w=800&q=80',
    category: 'Music & Food',
    rating: 4.97,
    reviewsCount: 95,
    duration: '4 hrs',
    price: 50,
    guide: {
      name: 'Tunde A.',
      avatar: 'https://images.unsplash.com/photo-1501196354995-cbb51c65aaea?auto=format&fit=crop&w=120&q=80',
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
      
      <div class="flex flex-col sm:flex-row sm:items-end justify-between mb-8 gap-4">
        <div>
          <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-emerald-100/80 border border-emerald-200/60 text-emerald-800 text-xs font-bold uppercase tracking-wider mb-3">
            <span>🌍</span> Top Rated in Africa
          </div>
          <h2 class="font-heading text-3xl sm:text-4xl font-black text-zinc-900 tracking-tight">
            Unforgettable African Adventures
          </h2>
          <p class="mt-2 text-sm sm:text-base text-zinc-600 max-w-xl font-sans">
            Book top-rated local hosts for private safari treks, medina food crawls, and vibrant coastal escapes.
          </p>
        </div>

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
          <div class="relative h-52 w-full overflow-hidden bg-zinc-100">
            <img 
              :src="tour.image" 
              :alt="tour.title"
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
              loading="lazy"
            />
            
            <span class="absolute top-3 left-3 bg-zinc-900/80 backdrop-blur-md text-white text-[11px] font-semibold px-2.5 py-1 rounded-full font-sans">
              {{ tour.category }}
            </span>

            <div class="absolute bottom-3 left-3 bg-white/90 backdrop-blur-md px-2.5 py-1 rounded-full flex items-center gap-1 text-xs font-bold text-zinc-900 shadow-sm">
              <span class="text-amber-500">★</span>
              <span class="font-heading">{{ tour.rating }}</span>
              <span class="text-zinc-400 font-normal font-sans">({{ tour.reviewsCount }})</span>
            </div>
          </div>

          <div class="p-5 flex-1 flex flex-col justify-between">
            <div>
              <div class="flex items-center justify-between text-xs text-zinc-500 font-semibold mb-2 font-sans">
                <span class="flex items-center gap-1 text-emerald-700">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-3.5 h-3.5">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z" />
                    <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
                  </svg>
                  {{ tour.location }}
                </span>
                <span>⏱️ {{ tour.duration }}</span>
              </div>

              <h3 class="font-heading text-base font-bold text-zinc-900 line-clamp-2 leading-snug group-hover:text-emerald-600 transition-colors">
                {{ tour.title }}
              </h3>
            </div>

            <div class="mt-6 pt-4 border-t border-zinc-100 flex items-center justify-between">
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
                  <p class="font-bold text-zinc-900 leading-none font-sans">{{ tour.guide.name }}</p>
                  <p class="text-[10px] text-zinc-400 font-medium font-sans">Local Host</p>
                </div>
              </div>

              <div class="text-right">
                <p class="text-[10px] uppercase tracking-wider font-bold text-zinc-400 font-sans">From</p>
                <p class="font-heading text-base font-black text-zinc-900">${{ tour.price }} <span class="font-sans text-xs font-normal text-zinc-500">/ person</span></p>
              </div>
            </div>

          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.scrollbar-none::-webkit-scrollbar {
  display: none;
}
</style>