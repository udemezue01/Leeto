<script setup>
import { ref } from 'vue'

const activeImage = ref(0)
const selectedDate = ref('')
const guestCount = ref(2)

// Video & Modal State
const isPlayingVideo = ref(false)
const showDmModal = ref(false)
const showReviewModal = ref(false)

const dmMessage = ref('')
const newReview = ref({
  author: '',
  rating: 5,
  comment: ''
})

const tour = ref({
  title: 'Ha Long Bay: Secret Caves & Floating Villages Kayak Tour',
  location: 'Ha Long Bay, Vietnam',
  rating: 4.98,
  reviewCount: 128,
  pricePerPerson: 85,
  duration: 'Full Day (8 Hours)',
  groupSize: 'Max 8 people',
  languages: ['English', 'Vietnamese'],
  cancellation: 'Free cancellation up to 24h before',
  images: [
    'https://images.unsplash.com/photo-1528127269322-539801943592?auto=format&fit=crop&w=1200&q=80',
    'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1552465011-b4e21bf6e79a?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1503899036084-c55cdd92da26?auto=format&fit=crop&w=800&q=80'
  ],
  guide: {
    name: 'Minh Tran',
    title: 'Certified Ha Long Bay Native Guide',
    avatar: 'https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=200&q=80',
    videoPoster: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=1000&q=80',
    videoUrl: 'https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ForBiggerBlazes.mp4',
    tripsLed: 340,
    rating: 5.0,
    bio: 'Born and raised in a floating village in Ha Long Bay. I have been guiding travelers through hidden lagoons and cave ecosystems for over 8 years.'
  },
  highlights: [
    'Kayak through secluded limestone caves away from crowds',
    'Enjoy an authentic home-cooked seafood lunch on a floating house',
    'Learn traditional fishing techniques from local villagers',
    'Round-trip private boat transport with safety gear provided'
  ],
  itinerary: [
    { time: '08:00 AM', title: 'Hotel Pickup & Harbor Transfer', desc: 'Meet your guide at your hotel lobby for transport to Tuan Chau Harbor.' },
    { time: '09:30 AM', title: 'Cruise to Secret Lagoon', desc: 'Board our private wooden boat and sail into quieter waters.' },
    { time: '11:00 AM', title: 'Kayaking & Cave Exploration', desc: 'Navigate narrow cave passages into untouched hidden lagoons.' },
    { time: '01:00 PM', title: 'Floating Village Seafood Feast', desc: 'Eat fresh lunch hosted by local fishermen inside their floating home.' },
    { time: '04:00 PM', title: 'Return Journey', desc: 'Relax on deck during golden hour as we cruise back to harbor.' }
  ]
})

const reviews = ref([
  {
    id: 1,
    author: 'Sarah Jenkins',
    avatar: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?auto=format&fit=crop&w=150&q=80',
    date: 'October 2025',
    rating: 5,
    comment: 'Minh took us to spots where there wasn’t a single other boat around! The food on the floating house was the best meal of our Vietnam trip.'
  },
  {
    id: 2,
    author: 'David Chen',
    avatar: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&w=150&q=80',
    date: 'September 2025',
    rating: 5,
    comment: 'Unbelievable experience. Kayaking through the dark cave opening into the hidden lake felt like stepping into another world.'
  }
])

const handleBooking = () => {
  alert(`Booking request sent for ${guestCount.value} guest(s) on ${selectedDate.value || 'selected date'}!`)
}

const handleSendDm = () => {
  if (!dmMessage.value.trim()) return
  alert(`Direct message sent to ${tour.value.guide.name}!`)
  dmMessage.value = ''
  showDmModal.value = false
}

const handleAddReview = () => {
  if (!newReview.value.author || !newReview.value.comment) return
  reviews.value.unshift({
    id: Date.now(),
    author: newReview.value.author,
    avatar: 'https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?auto=format&fit=crop&w=150&q=80',
    date: 'Just now',
    rating: Number(newReview.value.rating),
    comment: newReview.value.comment
  })
  tour.value.reviewCount++
  newReview.value = { author: '', rating: 5, comment: '' }
  showReviewModal.value = false
}
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen text-zinc-900">
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-10">
      
      <div class="space-y-4 text-left">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
          Verified Local Tour
        </div>

        <h1 class="font-heading text-3xl sm:text-4xl lg:text-5xl font-black tracking-tight leading-[1.15]">
          {{ tour.title }}
        </h1>

        <div class="flex flex-wrap items-center gap-4 text-sm font-medium text-zinc-600">
          <div class="flex items-center gap-1 text-amber-500 font-bold">
            <svg class="w-4 h-4 fill-amber-400 text-amber-400 shrink-0" viewBox="0 0 20 20">
              <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
            </svg>
            <span class="font-heading text-zinc-900">{{ tour.rating }}</span>
            <span class="text-zinc-500 font-normal">({{ tour.reviewCount }} reviews)</span>
          </div>
          <span>•</span>
          <div class="flex items-center gap-1">
            <svg class="w-4 h-4 text-emerald-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/></svg>
            <span>{{ tour.location }}</span>
          </div>
          <span>•</span>
          <span class="px-2.5 py-0.5 rounded-md bg-stone-200/70 text-xs font-bold text-zinc-700">Small Group</span>
        </div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-4">
        <div class="lg:col-span-8 relative h-72 sm:h-96 lg:h-[480px] rounded-3xl overflow-hidden bg-zinc-900 border border-zinc-200/80 shadow-md">
          <img :src="tour.images[activeImage]" :alt="tour.title" class="w-full h-full object-cover transition-all duration-300" />
        </div>
        <div class="lg:col-span-4 grid grid-cols-3 lg:grid-cols-1 gap-3 h-full">
          <button 
            v-for="(img, idx) in tour.images.slice(1)" 
            :key="idx" 
            @click="activeImage = idx + 1"
            class="relative h-24 sm:h-32 lg:h-[150px] rounded-2xl overflow-hidden border-2 transition-all"
            :class="activeImage === idx + 1 ? 'border-emerald-600 ring-2 ring-emerald-600/30' : 'border-transparent opacity-80 hover:opacity-100'"
          >
            <img :src="img" class="w-full h-full object-cover" />
          </button>
        </div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-8 items-start">
        
        <div class="lg:col-span-7 space-y-12">
          
          <div class="grid grid-cols-2 sm:grid-cols-4 gap-4 p-5 bg-white rounded-2xl border border-zinc-200/80 shadow-sm">
            <div>
              <p class="text-xs text-zinc-400 font-medium">Duration</p>
              <p class="font-heading text-sm font-bold text-zinc-900 mt-0.5">{{ tour.duration }}</p>
            </div>
            <div>
              <p class="text-xs text-zinc-400 font-medium">Group Size</p>
              <p class="font-heading text-sm font-bold text-zinc-900 mt-0.5">{{ tour.groupSize }}</p>
            </div>
            <div>
              <p class="text-xs text-zinc-400 font-medium">Languages</p>
              <p class="font-heading text-sm font-bold text-zinc-900 mt-0.5">{{ tour.languages.join(', ') }}</p>
            </div>
            <div>
              <p class="text-xs text-zinc-400 font-medium">Flexibility</p>
              <p class="font-heading text-sm font-bold text-emerald-600 mt-0.5">Free Cancel</p>
            </div>
          </div>

          <div class="space-y-4">
            <div class="flex items-center justify-between">
              <h2 class="font-heading text-2xl font-bold text-zinc-900">Meet Your Guide in Video</h2>
              <span class="text-xs font-bold text-emerald-600 bg-emerald-50 border border-emerald-200/70 px-2.5 py-1 rounded-full flex items-center gap-1.5">
                <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
                Video Intro
              </span>
            </div>

            <div class="relative rounded-3xl overflow-hidden bg-zinc-900 border border-zinc-200/80 shadow-lg aspect-video">
              <video 
                v-if="isPlayingVideo" 
                controls 
                autoplay 
                class="w-full h-full object-cover"
              >
                <source :src="tour.guide.videoUrl" type="video/mp4" />
                Your browser does not support video playback.
              </video>

              <div v-else class="relative w-full h-full">
                <img :src="tour.guide.videoPoster" alt="Guide Video Showcase" class="w-full h-full object-cover opacity-80" />
                <div class="absolute inset-0 bg-gradient-to-t from-zinc-950/80 via-zinc-950/30 to-transparent"></div>
                
                <button 
                  @click="isPlayingVideo = true" 
                  class="absolute inset-0 m-auto w-16 h-16 sm:w-20 sm:h-20 rounded-full bg-white/90 hover:bg-emerald-600 text-zinc-900 hover:text-white transition-all duration-300 shadow-2xl flex items-center justify-center group transform hover:scale-110"
                >
                  <svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" class="w-8 h-8 ml-1 group-hover:scale-105 transition-transform" viewBox="0 0 24 24">
                    <path d="M8 5v14l11-7z" />
                  </svg>
                </button>

                <div class="absolute bottom-4 left-4 right-4 text-white flex items-center justify-between">
                  <div class="flex items-center gap-3">
                    <img :src="tour.guide.avatar" class="w-10 h-10 rounded-full border-2 border-white/80 object-cover" />
                    <div>
                      <p class="font-heading text-sm font-bold text-white leading-tight">Watch {{ tour.guide.name }}'s Welcome Video</p>
                      <p class="text-xs text-stone-300 font-medium">1 min intro to this tour</p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="bg-white p-6 rounded-3xl border border-zinc-200/80 shadow-md space-y-5">
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4">
              <div class="flex items-center gap-4">
                <div class="relative">
                  <img :src="tour.guide.avatar" :alt="tour.guide.name" class="w-16 h-16 rounded-2xl object-cover" />
                  <span class="absolute -bottom-1 -right-1 w-5 h-5 bg-emerald-500 rounded-full border-2 border-white flex items-center justify-center">
                    <svg class="w-3 h-3 text-white stroke-[3]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5"/></svg>
                  </span>
                </div>
                <div>
                  <div class="flex items-center gap-2">
                    <h3 class="font-heading text-lg font-bold text-zinc-900">{{ tour.guide.name }}</h3>
                    <span class="text-xs font-bold text-emerald-700 bg-emerald-100 px-2 py-0.5 rounded-md">Host</span>
                  </div>
                  <p class="text-xs text-zinc-500 font-medium">{{ tour.guide.title }}</p>
                  <p class="text-xs text-amber-500 font-bold mt-1 flex items-center gap-1">
                    <svg class="w-3.5 h-3.5 fill-amber-400 text-amber-400 shrink-0" viewBox="0 0 20 20">
                      <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
                    </svg>
                    <span>{{ tour.guide.rating }}</span> 
                    <span class="text-zinc-400 font-normal">({{ tour.guide.tripsLed }} tours led)</span>
                  </p>
                </div>
              </div>

              <button 
                @click="showDmModal = true"
                class="px-5 py-2.5 bg-stone-100 hover:bg-zinc-900 hover:text-white text-zinc-900 font-bold text-xs rounded-xl border border-zinc-200/80 transition-all flex items-center justify-center gap-2 shrink-0 shadow-sm"
              >
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4 text-emerald-600">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M8.625 12a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0H8.25m4.125 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0h-.375m4.125 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0h-.375M21 12c0 4.556-4.03 8.25-9 8.25a9.764 9.764 0 01-2.555-.337A5.972 5.972 0 015.41 20.97a.75.75 0 01-1.074-.85 5.97 5.97 0 00.627-2.83A7.92 7.92 0 013 12c0-4.556 4.03-8.25 9-8.25s9 3.694 9 8.25z" />
                </svg>
                <span>Send DM to Guide</span>
              </button>
            </div>

            <p class="text-sm text-zinc-600 leading-relaxed font-medium">{{ tour.guide.bio }}</p>
          </div>

          <div class="space-y-4">
            <h2 class="font-heading text-2xl font-bold text-zinc-900">Experience Highlights</h2>
            <ul class="grid grid-cols-1 gap-3">
              <li v-for="(item, index) in tour.highlights" :key="index" class="flex items-start gap-3 text-sm text-zinc-600 font-medium leading-relaxed">
                <span class="w-5 h-5 rounded-full bg-emerald-100 text-emerald-700 flex items-center justify-center shrink-0 mt-0.5">
                  <svg class="w-3.5 h-3.5 text-emerald-700 stroke-[3]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5"/></svg>
                </span>
                <span>{{ item }}</span>
              </li>
            </ul>
          </div>

          <div class="space-y-6">
            <h2 class="font-heading text-2xl font-bold text-zinc-900">Tour Schedule</h2>
            <div class="space-y-6 relative before:absolute before:inset-0 before:left-3.5 before:w-0.5 before:bg-zinc-200">
              <div v-for="(step, idx) in tour.itinerary" :key="idx" class="relative flex items-start gap-6">
                <div class="w-7 h-7 rounded-full bg-zinc-900 border-4 border-stone-50 text-white font-bold text-xs flex items-center justify-center shrink-0 z-10">
                  {{ idx + 1 }}
                </div>
                <div class="bg-white p-4 rounded-2xl border border-zinc-200/70 flex-1 shadow-sm">
                  <span class="text-xs font-bold text-emerald-600 uppercase tracking-wider">{{ step.time }}</span>
                  <h4 class="font-heading text-base font-bold text-zinc-900 mt-0.5">{{ step.title }}</h4>
                  <p class="text-sm text-zinc-600 mt-1 leading-relaxed font-medium">{{ step.desc }}</p>
                </div>
              </div>
            </div>
          </div>

          <div class="space-y-6 pt-4">
            <div class="flex flex-wrap items-center justify-between gap-4">
              <div>
                <h2 class="font-heading text-2xl font-bold text-zinc-900">Guest Reviews</h2>
                <span class="font-heading text-amber-500 font-bold text-sm inline-flex items-center gap-1">
                  <svg class="w-4 h-4 fill-amber-400 text-amber-400 shrink-0" viewBox="0 0 20 20">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
                  </svg>
                  <span>{{ tour.rating }} / 5 rating</span>
                </span>
              </div>

              <button 
                @click="showReviewModal = true"
                class="px-4 py-2 bg-emerald-600 hover:bg-emerald-700 text-white font-bold text-xs rounded-xl shadow-md transition-all flex items-center gap-2"
              >
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M16.862 4.487l1.687-1.688a1.875 1.875 0 112.652 2.652L10.582 16.07a4.5 4.5 0 01-1.897 1.13L6 18l.8-2.685a4.5 4.5 0 011.13-1.897l8.932-8.931zm0 0L19.5 7.125M18 14v4.75A2.25 2.25 0 0115.75 21H5.25A2.25 2.25 0 013 18.75V8.25A2.25 2.25 0 015.25 6H10" />
                </svg>
                <span>Leave a Review</span>
              </button>
            </div>

            <div class="space-y-4">
              <div v-for="rev in reviews" :key="rev.id" class="bg-white p-5 rounded-2xl border border-zinc-200/80 space-y-3 shadow-sm">
                <div class="flex items-center justify-between">
                  <div class="flex items-center gap-3">
                    <img :src="rev.avatar" :alt="rev.author" class="w-10 h-10 rounded-full object-cover" />
                    <div>
                      <h4 class="font-heading text-sm font-bold text-zinc-900">{{ rev.author }}</h4>
                      <p class="text-xs text-zinc-400 font-medium">{{ rev.date }}</p>
                    </div>
                  </div>
                  <div class="flex items-center gap-0.5">
                    <svg v-for="n in rev.rating" :key="n" class="w-3.5 h-3.5 fill-amber-400 text-amber-400" viewBox="0 0 20 20">
                      <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
                    </svg>
                  </div>
                </div>
                <p class="text-sm text-zinc-600 leading-relaxed font-medium">"{{ rev.comment }}"</p>
              </div>
            </div>
          </div>

        </div>

        <div class="lg:col-span-5 relative lg:sticky lg:top-8">
          <div class="bg-white p-6 sm:p-8 rounded-3xl shadow-xl shadow-zinc-200/60 border border-zinc-200/80 space-y-6">
            
            <div class="flex items-baseline justify-between border-b border-zinc-100 pb-5">
              <div>
                <span class="font-heading text-3xl font-black text-zinc-900">${{ tour.pricePerPerson }}</span>
                <span class="text-zinc-500 text-sm font-medium"> / person</span>
              </div>
              <span class="text-xs font-bold text-emerald-700 bg-emerald-100 px-2.5 py-1 rounded-full">Best Price Guaranteed</span>
            </div>

            <div class="space-y-4">
              <div class="space-y-1.5">
                <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Select Date</label>
                <div class="relative flex items-center px-3.5 py-3 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                  <input type="date" v-model="selectedDate" class="w-full bg-transparent text-sm font-semibold text-zinc-900 focus:outline-none cursor-pointer" />
                </div>
              </div>

              <div class="space-y-1.5">
                <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Guests</label>
                <div class="relative flex items-center px-3.5 py-3 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                  <select v-model="guestCount" class="w-full bg-transparent text-sm font-semibold text-zinc-900 focus:outline-none cursor-pointer">
                    <option :value="1">1 Guest</option>
                    <option :value="2">2 Guests</option>
                    <option :value="4">4 Guests</option>
                    <option :value="6">6 Guests</option>
                  </select>
                </div>
              </div>
            </div>

            <div class="space-y-2 pt-2 text-sm text-zinc-600 font-medium">
              <div class="flex justify-between">
                <span>${{ tour.pricePerPerson }} x {{ guestCount }} guests</span>
                <span class="font-bold text-zinc-900">${{ tour.pricePerPerson * guestCount }}</span>
              </div>
              <div class="flex justify-between">
                <span>Local guide & gear fee</span>
                <span class="text-emerald-600 font-bold">Included</span>
              </div>
              <div class="border-t border-zinc-100 pt-3 flex justify-between text-base font-bold text-zinc-900">
                <span>Total</span>
                <span class="font-heading font-black text-lg">${{ tour.pricePerPerson * guestCount }}</span>
              </div>
            </div>

            <button 
              @click="handleBooking" 
              class="w-full py-4 bg-zinc-900 hover:bg-emerald-600 text-white font-bold text-base rounded-xl shadow-md hover:shadow-emerald-600/20 transition-all duration-200 flex items-center justify-center gap-2 group"
            >
              <span>Reserve Your Spot</span>
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4 group-hover:translate-x-1 transition-transform">
                <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
              </svg>
            </button>

            <div class="flex items-center gap-3 pt-2 text-xs text-zinc-500 font-medium">
              <div class="w-8 h-8 rounded-lg bg-stone-100 text-zinc-700 flex items-center justify-center font-bold shrink-0">
                <svg class="w-4 h-4 text-zinc-700" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75m-3-7.036A11.959 11.959 0 013.598 6 11.99 11.99 0 003 9.749c0 5.592 3.824 10.29 9 11.623 5.176-1.332 9-6.03 9-11.622 0-1.31-.21-2.571-.598-3.751A11.959 11.959 0 0112 2.714z" />
                </svg>
              </div>
              <p>Reserve now & pay later. No upfront charges for instant reservation.</p>
            </div>

          </div>
        </div>

      </div>

    </div>

    <div v-if="showDmModal" class="fixed inset-0 bg-zinc-950/60 backdrop-blur-sm z-50 flex items-center justify-center p-4">
      <div class="bg-white p-6 sm:p-8 rounded-3xl max-w-lg w-full border border-zinc-200 shadow-2xl space-y-5 relative">
        <div class="flex items-center justify-between border-b border-zinc-100 pb-4">
          <div class="flex items-center gap-3">
            <img :src="tour.guide.avatar" class="w-10 h-10 rounded-xl object-cover" />
            <div>
              <h3 class="font-heading text-base font-bold text-zinc-900">Message {{ tour.guide.name }}</h3>
              <p class="text-xs text-zinc-500 font-medium">Typically responds within 1 hour</p>
            </div>
          </div>
          <button @click="showDmModal = false" class="p-1 rounded-lg hover:bg-stone-100 transition-colors">
            <svg class="w-5 h-5 text-zinc-400 hover:text-zinc-900" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>

        <div class="space-y-2">
          <label class="text-xs font-bold uppercase text-zinc-700">Your Message</label>
          <textarea 
            v-model="dmMessage" 
            rows="4" 
            placeholder="Ask about custom pickup times, dietary constraints, or special requests..." 
            class="w-full p-3 bg-stone-50 rounded-xl border border-zinc-200 text-sm font-medium focus:outline-none focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 transition-all"
          ></textarea>
        </div>

        <div class="flex justify-end gap-3 pt-2">
          <button @click="showDmModal = false" class="px-5 py-2.5 bg-stone-100 hover:bg-stone-200 text-zinc-700 font-bold text-xs rounded-xl transition-all">Cancel</button>
          <button @click="handleSendDm" class="px-5 py-2.5 bg-zinc-900 hover:bg-emerald-600 text-white font-bold text-xs rounded-xl shadow-md transition-all">Send Direct Message</button>
        </div>
      </div>
    </div>

    <div v-if="showReviewModal" class="fixed inset-0 bg-zinc-950/60 backdrop-blur-sm z-50 flex items-center justify-center p-4">
      <div class="bg-white p-6 sm:p-8 rounded-3xl max-w-lg w-full border border-zinc-200 shadow-2xl space-y-5 relative">
        <div class="flex items-center justify-between border-b border-zinc-100 pb-4">
          <h3 class="font-heading text-lg font-bold text-zinc-900">Write a Tour Review</h3>
          <button @click="showReviewModal = false" class="p-1 rounded-lg hover:bg-stone-100 transition-colors">
            <svg class="w-5 h-5 text-zinc-400 hover:text-zinc-900" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>

        <div class="space-y-4">
          <div class="space-y-1">
            <label class="text-xs font-bold uppercase text-zinc-700">Your Name</label>
            <input 
              v-model="newReview.author" 
              type="text" 
              placeholder="e.g. Alex Smith" 
              class="w-full p-3 bg-stone-50 rounded-xl border border-zinc-200 text-sm font-medium focus:outline-none focus:border-emerald-600"
            />
          </div>

          <div class="space-y-1">
            <label class="text-xs font-bold uppercase text-zinc-700">Rating</label>
            <select v-model="newReview.rating" class="w-full p-3 bg-stone-50 rounded-xl border border-zinc-200 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600">
              <option :value="5">5 - Excellent</option>
              <option :value="4">4 - Very Good</option>
              <option :value="3">3 - Average</option>
              <option :value="2">2 - Poor</option>
              <option :value="1">1 - Terrible</option>
            </select>
          </div>

          <div class="space-y-1">
            <label class="text-xs font-bold uppercase text-zinc-700">Review</label>
            <textarea 
              v-model="newReview.comment" 
              rows="3" 
              placeholder="Share details of your experience..." 
              class="w-full p-3 bg-stone-50 rounded-xl border border-zinc-200 text-sm font-medium focus:outline-none focus:border-emerald-600"
            ></textarea>
          </div>
        </div>

        <div class="flex justify-end gap-3 pt-2">
          <button @click="showReviewModal = false" class="px-5 py-2.5 bg-stone-100 hover:bg-stone-200 text-zinc-700 font-bold text-xs rounded-xl transition-all">Cancel</button>
          <button @click="handleAddReview" class="px-5 py-2.5 bg-emerald-600 hover:bg-emerald-700 text-white font-bold text-xs rounded-xl shadow-md transition-all">Submit Review</button>
        </div>
      </div>
    </div>

  </section>
</template>