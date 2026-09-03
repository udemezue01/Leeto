<script setup>
import { ref, computed } from 'vue'

// Interactive State
const activeImage = ref(0)
const activeMediaTab = ref('gallery') // 'gallery' | 'trailer' | 'guideVideo'
const selectedDate = ref('')

// Guest Counts
const adultGuests = ref(2)
const childGuests = ref(0)
const seniorGuests = ref(0)

// Add-ons Selection
const selectedAddons = ref([])

// Modals
const showDmModal = ref(false)
const showReviewModal = ref(false)
const dmMessage = ref('')
const newReview = ref({
  author: '',
  rating: 5,
  comment: ''
})

// Detailed Tour Data Structure
const tour = ref({
  title: 'Ha Long Bay: Secret Caves & Floating Villages Kayak Tour',
  category: 'Adventure & Kayaking',
  tags: ['Family Friendly', 'Eco-Tour', 'Seafood Lunch', 'Cave Exploration', 'Small Group'],
  
  // Geography & Location
  location: {
    continent: 'Asia',
    country: 'Vietnam',
    region: 'Quảng Ninh Province',
    city: 'Ha Long Bay',
    meetingPoint: 'Tuan Chau International Passenger Port - Dock #12, Ward Tuan Chau, Ha Long City',
    meetingInstructions: 'Look for your guide wearing a green Leeto badge and holding a wooden welcome paddle by the main terminal clock tower.',
    coordinates: { lat: '20.9101° N', long: '107.0083° E' },
    dropOffPoint: 'Return transfer to Tuan Chau Harbor or your hotel lobby in Ha Long City.'
  },

  // Languages Spoken
  languages: {
    primary: 'English',
    additional: ['Vietnamese', 'French']
  },

  // Logistics & Policies
  logistics: {
    duration: 'Full Day (8 Hours)',
    bookingCutoff: '12 hours in advance',
    physicalLevel: 'Moderate (approx. 2 hours of light kayaking)',
    minAge: '6 years old',
    accessibility: 'Not wheelchair accessible due to cave steps and boat boarding.',
    cancellationPolicy: 'Flexible: Free cancellation up to 24 hours before tour start time.',
    groupType: 'Joinable Small Group',
    minParticipants: 2,
    maxParticipants: 8
  },

  // Pricing Structure
  pricing: {
    adult: 85,
    child: 55, // Ages 6-12
    senior: 75 // Ages 65+
  },

  // Add-ons
  availableAddons: [
    { id: 'gopro', name: 'GoPro 4K Video & Photo Package', price: 25, desc: 'Raw memory card + 15 edited hero shots' },
    { id: 'transfer', name: 'Private Hotel Pickup & Drop-off', price: 35, desc: 'Door-to-door roundtrip AC van transfer' },
    { id: 'seafood_upgrade', name: 'Premium Lobster Lunch Upgrade', price: 30, desc: 'Fresh local lobster dish added to meal' }
  ],

  // What's Included / Not Included
  inclusions: [
    'Professional English-speaking native guide',
    'Sea kayak rental & lightweight aluminum paddles',
    'Certified safety life jackets & dry bags',
    'Home-cooked seafood lunch on a floating village house',
    'All entrance fees to Ha Long Bay heritage zone',
    'Bottled spring water and fresh tropical fruit'
  ],
  exclusions: [
    'Gratuities & tips for local fishermen and guide',
    'Alcoholic beverages & canned sodas',
    'Personal travel insurance',
    'Hotel pickup (unless add-on is selected)'
  ],

  // What to bring & Health Safety
  whatToBring: [
    'Comfortable water shoes or sandals with strap',
    'Sunscreen (reef-safe preferred), hat & sunglasses',
    'Change of dry clothes and small towel',
    'Cash (VND) for personal snacks or souvenirs'
  ],
  healthSafety: [
    'CPR & First Aid certified lead guide',
    'Sanitized life jackets inspect prior to embarkation',
    'Emergency satellite communication on board',
    'Daily monitored weather and wave forecasting'
  ],

  // Media Gallery
  images: [
    'https://images.unsplash.com/photo-1528127269322-539801943592?auto=format&fit=crop&w=1200&q=80',
    'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1552465011-b4e21bf6e79a?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1503899036084-c55cdd92da26?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1544644181-1484b3fdfc62?auto=format&fit=crop&w=800&q=80',
    'https://images.unsplash.com/photo-1506929562872-bb421503ef21?auto=format&fit=crop&w=800&q=80'
  ],
  trailerVideoUrl: 'https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ForBiggerBlazes.mp4',

  // Guide Details
  guide: {
    name: 'Minh Tran',
    title: 'Certified Ha Long Bay Native Guide',
    avatar: 'https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=200&q=80',
    videoPoster: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=1000&q=80',
    videoUrl: 'https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4',
    tripsLed: 340,
    rating: 5.0,
    bio: 'Born and raised in a floating village in Ha Long Bay. I have been guiding travelers through hidden lagoons and cave ecosystems for over 8 years.'
  },

  // Description & Highlights
  description: 'Embark on a tranquil escape into the heart of Ha Long Bay. Leaving behind crowded cruise routes, our small-group kayak journey navigates narrow limestone passages to access untouched lagoons and ancient tidal caves. Experience authentic local culture with a home-cooked lunch hosted by floating village residents.',
  highlights: [
    'Kayak through secluded limestone caves away from commercial boats',
    'Enjoy an authentic home-cooked seafood lunch on a floating house',
    'Learn traditional fishing and pearl farming techniques from local villagers',
    'Navigate through hidden marine lagoons accessible only by small kayak',
    'Round-trip private wooden boat transport equipped with safety gear'
  ],

  // Itinerary
  itinerary: [
    { time: '08:00 AM', title: 'Port Meeting & Harbor Embarkation', desc: 'Meet Minh at Tuan Chau Port Dock #12 and board our private wooden tender boat.' },
    { time: '09:30 AM', title: 'Cruise to Ba Hang Secret Lagoon', desc: 'Sailing past iconic karsts into serene, restricted-access waters.' },
    { time: '11:00 AM', title: 'Kayaking through Luon Cave', desc: 'Paddle through a natural limestone tunnel opening into a hidden circular bay.' },
    { time: '01:00 PM', title: 'Floating Village Seafood Feast', desc: 'Savor freshly caught fish, prawns, and seasonal green vegetables prepared by host families.' },
    { time: '02:30 PM', title: 'Pearl Farm & Floating School Visit', desc: 'Discover how generations lived sustainably on the water.' },
    { time: '04:00 PM', title: 'Golden Hour Return Journey', desc: 'Relax on deck with fresh tea and fruit as we cruise back to port.' }
  ],

  rating: 4.98,
  reviewCount: 128
})

// Guest Reviews List
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

// Calculated Dynamic Total
const calculatedTotal = computed(() => {
  const basePrice = (adultGuests.value * tour.value.pricing.adult) + 
                    (childGuests.value * tour.value.pricing.child) + 
                    (seniorGuests.value * tour.value.pricing.senior)
  
  const addonsPrice = selectedAddons.value.reduce((sum, addonId) => {
    const item = tour.value.availableAddons.find(a => a.id === addonId)
    return sum + (item ? item.price : 0)
  }, 0)

  return basePrice + addonsPrice
})

const totalGuests = computed(() => adultGuests.value + childGuests.value + seniorGuests.value)

// Add-on Toggle
const toggleAddon = (id) => {
  const index = selectedAddons.value.indexOf(id)
  if (index === -1) {
    selectedAddons.value.push(id)
  } else {
    selectedAddons.value.splice(index, 1)
  }
}

// Handlers
const handleBooking = () => {
  if (totalGuests.value < tour.value.logistics.minParticipants) {
    alert(`This tour requires a minimum of ${tour.value.logistics.minParticipants} participants.`)
    return
  }
  alert(`Booking request submitted for ${totalGuests.value} guest(s) on ${selectedDate.value || 'selected date'}! Total: $${calculatedTotal.value}`)
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
        
        <div class="flex flex-wrap items-center gap-2 text-xs font-semibold text-zinc-500">
          <span class="px-3 py-1 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 font-bold uppercase tracking-wider">
            {{ tour.category }}
          </span>
          <span>•</span>
          <span>{{ tour.location.continent }}</span>
          <span>/</span>
          <span>{{ tour.location.country }}</span>
          <span>/</span>
          <span>{{ tour.location.region }}</span>
          <span>/</span>
          <span class="text-zinc-900 font-bold">{{ tour.location.city }}</span>
        </div>

        <h1 class="font-heading text-3xl sm:text-4xl lg:text-5xl font-black tracking-tight leading-[1.15] text-zinc-900">
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
            <svg class="w-4 h-4 text-emerald-600 shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"/><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"/></svg>
            <span>{{ tour.location.city }}, {{ tour.location.country }}</span>
          </div>
          <span>•</span>
          <span class="px-2.5 py-0.5 rounded-md bg-stone-200/70 text-xs font-bold text-zinc-700">{{ tour.logistics.groupType }}</span>
        </div>

        <div class="flex flex-wrap gap-2 pt-1">
          <span v-for="tag in tour.tags" :key="tag" class="px-2.5 py-1 rounded-lg bg-stone-200/60 text-zinc-700 text-xs font-semibold">
            #{{ tag }}
          </span>
        </div>
      </div>

      <div class="space-y-4">
        <div class="flex items-center gap-2 border-b border-zinc-200/80 pb-2">
          <button 
            @click="activeMediaTab = 'gallery'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all flex items-center gap-2"
            :class="activeMediaTab === 'gallery' ? 'bg-zinc-900 text-white shadow-md' : 'bg-white text-zinc-600 hover:bg-stone-100'"
          >
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 15.75l5.159-5.159a2.25 2.25 0 013.182 0l5.159 5.159m-1.5-1.5l1.409-1.409a2.25 2.25 0 013.182 0l2.909 2.909m-18 3.75h16.5a1.5 1.5 0 001.5-1.5V6a1.5 1.5 0 00-1.5-1.5H3.75A1.5 1.5 0 002.25 6v12a1.5 1.5 0 001.5 1.5zm10.5-11.25a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0z"/></svg>
            <span>Photo Gallery ({{ tour.images.length }})</span>
          </button>

          <button 
            @click="activeMediaTab = 'trailer'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all flex items-center gap-2"
            :class="activeMediaTab === 'trailer' ? 'bg-zinc-900 text-white shadow-md' : 'bg-white text-zinc-600 hover:bg-stone-100'"
          >
            <svg class="w-4 h-4 text-amber-500" fill="currentColor" viewBox="0 0 24 24"><path d="M8 5v14l11-7z"/></svg>
            <span>Tour Teaser Trailer</span>
          </button>

          <button 
            @click="activeMediaTab = 'guideVideo'"
            class="px-4 py-2 rounded-xl text-xs font-bold transition-all flex items-center gap-2"
            :class="activeMediaTab === 'guideVideo' ? 'bg-zinc-900 text-white shadow-md' : 'bg-white text-zinc-600 hover:bg-stone-100'"
          >
            <svg class="w-4 h-4 text-emerald-500" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M15.75 6a3.75 3.75 0 11-7.5 0 3.75 3.75 0 017.5 0zM4.501 20.118a7.5 7.5 0 0114.998 0A17.933 17.933 0 0112 21.75c-2.676 0-5.216-.584-7.499-1.632z"/></svg>
            <span>Meet {{ tour.guide.name }} (Guide Video)</span>
          </button>
        </div>

        <div v-if="activeMediaTab === 'gallery'" class="grid grid-cols-1 lg:grid-cols-12 gap-4">
          <div class="lg:col-span-8 relative h-72 sm:h-96 lg:h-[480px] rounded-3xl overflow-hidden bg-zinc-900 border border-zinc-200/80 shadow-md">
            <img :src="tour.images[activeImage]" :alt="tour.title" class="w-full h-full object-cover transition-all duration-300" />
            <div class="absolute bottom-4 left-4 bg-zinc-900/80 backdrop-blur-md px-3 py-1.5 rounded-full text-white text-xs font-medium">
              Image {{ activeImage + 1 }} of {{ tour.images.length }}
            </div>
          </div>
          <div class="lg:col-span-4 grid grid-cols-3 sm:grid-cols-5 lg:grid-cols-2 gap-3 h-full max-h-[480px] overflow-y-auto pr-1">
            <button 
              v-for="(img, idx) in tour.images" 
              :key="idx" 
              @click="activeImage = idx"
              class="relative h-24 sm:h-28 lg:h-[110px] rounded-2xl overflow-hidden border-2 transition-all"
              :class="activeImage === idx ? 'border-emerald-600 ring-2 ring-emerald-600/30' : 'border-transparent opacity-80 hover:opacity-100'"
            >
              <img :src="img" class="w-full h-full object-cover" />
            </button>
          </div>
        </div>

        <div v-else-if="activeMediaTab === 'trailer'" class="relative rounded-3xl overflow-hidden bg-zinc-900 border border-zinc-200/80 shadow-lg aspect-video max-h-[480px] mx-auto">
          <video controls autoplay class="w-full h-full object-cover">
            <source :src="tour.trailerVideoUrl" type="video/mp4" />
            Your browser does not support video playback.
          </video>
        </div>

        <div v-else-if="activeMediaTab === 'guideVideo'" class="relative rounded-3xl overflow-hidden bg-zinc-900 border border-zinc-200/80 shadow-lg aspect-video max-h-[480px] mx-auto">
          <video controls autoplay class="w-full h-full object-cover">
            <source :src="tour.guide.videoUrl" type="video/mp4" />
            Your browser does not support video playback.
          </video>
        </div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-8 items-start">
        
        <div class="lg:col-span-7 space-y-10">
          
          <div class="grid grid-cols-2 sm:grid-cols-3 gap-4 p-5 bg-white rounded-3xl border border-zinc-200/80 shadow-sm">
            <div>
              <p class="text-xs text-zinc-400 font-medium uppercase tracking-wider">Duration</p>
              <p class="font-heading text-sm font-bold text-zinc-900 mt-0.5">{{ tour.logistics.duration }}</p>
            </div>
            <div>
              <p class="text-xs text-zinc-400 font-medium uppercase tracking-wider">Group Limit</p>
              <p class="font-heading text-sm font-bold text-zinc-900 mt-0.5">{{ tour.logistics.minParticipants }} - {{ tour.logistics.maxParticipants }} people</p>
            </div>
            <div>
              <p class="text-xs text-zinc-400 font-medium uppercase tracking-wider">Primary Language</p>
              <p class="font-heading text-sm font-bold text-zinc-900 mt-0.5">{{ tour.languages.primary }}</p>
            </div>
            <div>
              <p class="text-xs text-zinc-400 font-medium uppercase tracking-wider">Physical Level</p>
              <p class="font-heading text-sm font-bold text-zinc-900 mt-0.5">{{ tour.logistics.physicalLevel }}</p>
            </div>
            <div>
              <p class="text-xs text-zinc-400 font-medium uppercase tracking-wider">Minimum Age</p>
              <p class="font-heading text-sm font-bold text-zinc-900 mt-0.5">{{ tour.logistics.minAge }}</p>
            </div>
            <div>
              <p class="text-xs text-zinc-400 font-medium uppercase tracking-wider">Booking Cut-off</p>
              <p class="font-heading text-sm font-bold text-emerald-600 mt-0.5">{{ tour.logistics.bookingCutoff }}</p>
            </div>
          </div>

          <div class="space-y-3">
            <h2 class="font-heading text-2xl font-bold text-zinc-900">About This Tour</h2>
            <p class="text-sm text-zinc-600 leading-relaxed font-medium">
              {{ tour.description }}
            </p>
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
            <h2 class="font-heading text-2xl font-bold text-zinc-900">Detailed Itinerary Schedule</h2>
            <div class="space-y-6 relative before:absolute before:inset-0 before:left-3.5 before:w-0.5 before:bg-zinc-200">
              <div v-for="(step, idx) in tour.itinerary" :key="idx" class="relative flex items-start gap-6">
                <div class="w-7 h-7 rounded-full bg-zinc-900 border-4 border-stone-50 text-white font-bold text-xs flex items-center justify-center shrink-0 z-10">
                  {{ idx + 1 }}
                </div>
                <div class="bg-white p-4.5 rounded-2xl border border-zinc-200/70 flex-1 shadow-sm space-y-1">
                  <span class="text-xs font-bold text-emerald-600 uppercase tracking-wider">{{ step.time }}</span>
                  <h4 class="font-heading text-base font-bold text-zinc-900">{{ step.title }}</h4>
                  <p class="text-sm text-zinc-600 leading-relaxed font-medium">{{ step.desc }}</p>
                </div>
              </div>
            </div>
          </div>

          <div class="space-y-4">
            <h2 class="font-heading text-2xl font-bold text-zinc-900">What's Included & Excluded</h2>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              
              <div class="bg-emerald-50/50 p-5 rounded-3xl border border-emerald-200/60 space-y-3">
                <h3 class="font-heading text-xs font-bold text-emerald-900 uppercase tracking-wider flex items-center gap-1.5">
                  <svg class="w-4 h-4 text-emerald-600" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5"/></svg>
                  What's Included
                </h3>
                <ul class="space-y-2 text-xs text-zinc-700 font-medium">
                  <li v-for="(inc, i) in tour.inclusions" :key="i" class="flex items-start gap-2">
                    <span class="text-emerald-600 font-bold">•</span>
                    <span>{{ inc }}</span>
                  </li>
                </ul>
              </div>

              <div class="bg-stone-100/70 p-5 rounded-3xl border border-zinc-200/80 space-y-3">
                <h3 class="font-heading text-xs font-bold text-zinc-500 uppercase tracking-wider flex items-center gap-1.5">
                  <svg class="w-4 h-4 text-zinc-400" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12"/></svg>
                  What's Not Included
                </h3>
                <ul class="space-y-2 text-xs text-zinc-600 font-medium">
                  <li v-for="(exc, i) in tour.exclusions" :key="i" class="flex items-start gap-2">
                    <span class="text-zinc-400 font-bold">•</span>
                    <span>{{ exc }}</span>
                  </li>
                </ul>
              </div>

            </div>
          </div>

          <div class="bg-white p-6 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <div class="flex items-center justify-between border-b border-zinc-100 pb-3">
              <h2 class="font-heading text-lg font-bold text-zinc-900">Meeting & End Point Logistics</h2>
              <span class="text-xs font-mono font-bold text-zinc-500 bg-stone-100 px-2.5 py-1 rounded-md">
                GPS: {{ tour.location.coordinates.lat }}, {{ tour.location.coordinates.long }}
              </span>
            </div>

            <div class="space-y-3 text-sm">
              <div>
                <p class="text-xs font-bold uppercase text-zinc-400">Meeting Address</p>
                <p class="font-semibold text-zinc-900 mt-0.5">{{ tour.location.meetingPoint }}</p>
              </div>

              <div>
                <p class="text-xs font-bold uppercase text-zinc-400">How to Find Your Guide</p>
                <p class="text-zinc-600 font-medium mt-0.5 leading-relaxed">{{ tour.location.meetingInstructions }}</p>
              </div>

              <div class="pt-2 border-t border-zinc-100">
                <p class="text-xs font-bold uppercase text-zinc-400">Drop-off / End Point</p>
                <p class="text-zinc-600 font-medium mt-0.5">{{ tour.location.dropOffPoint }}</p>
              </div>
            </div>
          </div>

          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <div class="bg-white p-5 rounded-3xl border border-zinc-200/80 shadow-sm space-y-3">
              <h3 class="font-heading text-xs font-bold text-zinc-900 uppercase tracking-wider">What to Bring</h3>
              <ul class="space-y-1.5 text-xs text-zinc-600 font-medium">
                <li v-for="(item, i) in tour.whatToBring" :key="i" class="flex items-center gap-2">
                  <span class="w-1.5 h-1.5 rounded-full bg-amber-500"></span>
                  <span>{{ item }}</span>
                </li>
              </ul>
            </div>

            <div class="bg-white p-5 rounded-3xl border border-zinc-200/80 shadow-sm space-y-3">
              <h3 class="font-heading text-xs font-bold text-zinc-900 uppercase tracking-wider">Health & Safety Measures</h3>
              <ul class="space-y-1.5 text-xs text-zinc-600 font-medium">
                <li v-for="(item, i) in tour.healthSafety" :key="i" class="flex items-center gap-2">
                  <span class="w-1.5 h-1.5 rounded-full bg-emerald-500"></span>
                  <span>{{ item }}</span>
                </li>
              </ul>
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
                    <span class="text-xs font-bold text-emerald-700 bg-emerald-100 px-2 py-0.5 rounded-md">Verified Host</span>
                  </div>
                  <p class="text-xs text-zinc-500 font-medium">{{ tour.guide.title }}</p>
                  <p class="text-xs text-zinc-500 font-medium mt-0.5">Languages: {{ tour.languages.primary }}, {{ tour.languages.additional.join(', ') }}</p>
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

          <div class="space-y-6 pt-4">
            <div class="flex flex-wrap items-center justify-between gap-4">
              <div>
                <h2 class="font-heading text-2xl font-bold text-zinc-900">Guest Reviews</h2>
                <span class="font-heading text-amber-500 font-bold text-sm inline-flex items-center gap-1">
                  <svg class="w-4 h-4 fill-amber-400 text-amber-400 shrink-0" viewBox="0 0 20 20">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
                  </svg>
                  <span>{{ tour.rating }} / 5 overall rating</span>
                </span>
              </div>

              <button 
                @click="showReviewModal = true"
                class="px-4 py-2 bg-emerald-600 hover:bg-emerald-700 text-white font-bold text-xs rounded-xl shadow-md transition-all flex items-center gap-2"
              >
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M16.862 4.487l1.687-1.688a1.875 1.875 0 112.652 2.652L10.582 16.07a4.5 4.5 0 01-1.897 1.13L6 18l.8-2.685a4.5 4.5 0 011.13-1.897l8.932-8.931zm0 0L19.5 7.125M18 14v4.75A2.25 2.25 0 0115.75 21H5.25A2.25 2.25 0 013 18.75V8.25A2.25 2.25 0 015.25 6H10" />
                </svg>
                <span>Write a Review</span>
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
                <span class="font-heading text-3xl font-black text-zinc-900">${{ tour.pricing.adult }}</span>
                <span class="text-zinc-500 text-sm font-medium"> / adult</span>
              </div>
              <span class="text-xs font-bold text-emerald-700 bg-emerald-100 px-2.5 py-1 rounded-full">
                {{ tour.logistics.cancellationPolicy.split(':')[0] }}
              </span>
            </div>

            <div class="space-y-1.5">
              <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Select Date</label>
              <div class="relative flex items-center px-3.5 py-3 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                <input type="date" v-model="selectedDate" class="w-full bg-transparent text-sm font-semibold text-zinc-900 focus:outline-none cursor-pointer" />
              </div>
            </div>

            <div class="space-y-3">
              <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Select Travelers</label>
              
              <div class="flex items-center justify-between p-3 bg-stone-50 rounded-xl border border-zinc-200/70">
                <div>
                  <p class="text-xs font-bold text-zinc-900">Adults (13-64 yrs)</p>
                  <p class="text-[11px] text-zinc-500">${{ tour.pricing.adult }} / person</p>
                </div>
                <div class="flex items-center gap-3">
                  <button @click="adultGuests = Math.max(1, adultGuests - 1)" class="w-7 h-7 rounded-lg bg-white border border-zinc-300 font-bold text-zinc-700 hover:bg-stone-200 flex items-center justify-center">-</button>
                  <span class="font-heading font-bold text-sm text-zinc-900">{{ adultGuests }}</span>
                  <button @click="adultGuests++" class="w-7 h-7 rounded-lg bg-white border border-zinc-300 font-bold text-zinc-700 hover:bg-stone-200 flex items-center justify-center">+</button>
                </div>
              </div>

              <div class="flex items-center justify-between p-3 bg-stone-50 rounded-xl border border-zinc-200/70">
                <div>
                  <p class="text-xs font-bold text-zinc-900">Children (6-12 yrs)</p>
                  <p class="text-[11px] text-zinc-500">${{ tour.pricing.child }} / person</p>
                </div>
                <div class="flex items-center gap-3">
                  <button @click="childGuests = Math.max(0, childGuests - 1)" class="w-7 h-7 rounded-lg bg-white border border-zinc-300 font-bold text-zinc-700 hover:bg-stone-200 flex items-center justify-center">-</button>
                  <span class="font-heading font-bold text-sm text-zinc-900">{{ childGuests }}</span>
                  <button @click="childGuests++" class="w-7 h-7 rounded-lg bg-white border border-zinc-300 font-bold text-zinc-700 hover:bg-stone-200 flex items-center justify-center">+</button>
                </div>
              </div>

              <div class="flex items-center justify-between p-3 bg-stone-50 rounded-xl border border-zinc-200/70">
                <div>
                  <p class="text-xs font-bold text-zinc-900">Seniors (65+ yrs)</p>
                  <p class="text-[11px] text-zinc-500">${{ tour.pricing.senior }} / person</p>
                </div>
                <div class="flex items-center gap-3">
                  <button @click="seniorGuests = Math.max(0, seniorGuests - 1)" class="w-7 h-7 rounded-lg bg-white border border-zinc-300 font-bold text-zinc-700 hover:bg-stone-200 flex items-center justify-center">-</button>
                  <span class="font-heading font-bold text-sm text-zinc-900">{{ seniorGuests }}</span>
                  <button @click="seniorGuests++" class="w-7 h-7 rounded-lg bg-white border border-zinc-300 font-bold text-zinc-700 hover:bg-stone-200 flex items-center justify-center">+</button>
                </div>
              </div>
            </div>

            <div class="space-y-2 pt-1">
              <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Optional Tour Add-ons</label>
              
              <div 
                v-for="addon in tour.availableAddons" 
                :key="addon.id"
                @click="toggleAddon(addon.id)"
                class="p-3 rounded-xl border transition-all cursor-pointer flex items-start justify-between gap-3"
                :class="selectedAddons.includes(addon.id) ? 'border-emerald-600 bg-emerald-50/40' : 'border-zinc-200/80 bg-stone-50/50 hover:border-zinc-300'"
              >
                <div class="flex items-start gap-2.5">
                  <input type="checkbox" :checked="selectedAddons.includes(addon.id)" class="mt-0.5 accent-emerald-600 rounded cursor-pointer" />
                  <div>
                    <p class="text-xs font-bold text-zinc-900">{{ addon.name }}</p>
                    <p class="text-[11px] text-zinc-500 font-medium">{{ addon.desc }}</p>
                  </div>
                </div>
                <span class="text-xs font-bold text-zinc-900 shrink-0">+${{ addon.price }}</span>
              </div>
            </div>

            <div class="space-y-2 pt-3 border-t border-zinc-100 text-sm text-zinc-600 font-medium">
              <div v-if="adultGuests > 0" class="flex justify-between">
                <span>Adults (${{ tour.pricing.adult }} x {{ adultGuests }})</span>
                <span class="font-bold text-zinc-900">${{ adultGuests * tour.pricing.adult }}</span>
              </div>
              
              <div v-if="childGuests > 0" class="flex justify-between">
                <span>Children (${{ tour.pricing.child }} x {{ childGuests }})</span>
                <span class="font-bold text-zinc-900">${{ childGuests * tour.pricing.child }}</span>
              </div>

              <div v-if="seniorGuests > 0" class="flex justify-between">
                <span>Seniors (${{ tour.pricing.senior }} x {{ seniorGuests }})</span>
                <span class="font-bold text-zinc-900">${{ seniorGuests * tour.pricing.senior }}</span>
              </div>

              <div v-if="selectedAddons.length > 0" class="flex justify-between text-emerald-700">
                <span>Add-ons Total</span>
                <span class="font-bold">${{ selectedAddons.reduce((s, id) => s + (tour.availableAddons.find(a => a.id === id)?.price || 0), 0) }}</span>
              </div>

              <div class="border-t border-zinc-100 pt-3 flex justify-between text-base font-bold text-zinc-900">
                <span>Total Amount</span>
                <span class="font-heading font-black text-xl text-emerald-600">${{ calculatedTotal }}</span>
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
              <p>{{ tour.logistics.cancellationPolicy }}</p>
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