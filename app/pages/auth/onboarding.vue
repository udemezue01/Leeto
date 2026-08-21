<script setup>
import { ref, computed } from 'vue'

// Account Role State
const accountType = ref('traveller') // 'traveller' | 'guide'

// Form Data State
const profile = ref({
  fullName: 'Alex Rivera',
  username: 'alex_explores',
  country: 'Spain',
  bio: 'Passionate about discovering hidden local food spots, historical architecture, and off-the-beaten-path trails.',
  avatarUrl: 'https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=400&q=80',
  languages: ['English', 'Spanish'],
  socials: {
    instagram: 'alex.explores',
    twitter: '',
    website: 'https://alexrivera.travel'
  },
  // Traveller-specific fields
  traveller: {
    travelStyles: ['Foodie', 'Adventure', 'Solo Travel'],
    currency: 'USD'
  },
  // Guide-specific fields
  guide: {
    hourlyRate: 45,
    city: 'Barcelona',
    specialties: ['Food & Drinks', 'History & Walking', 'Architecture'],
    introVideoUrl: '',
    yearsExperience: '3-5 years',
    idVerified: false
  }
})

// Sample Avatar Options
const sampleAvatars = [
  'https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=400&q=80',
  'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&w=400&q=80',
  'https://images.unsplash.com/photo-1494790108377-be9c29b29330?auto=format&fit=crop&w=400&q=80',
  'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?auto=format&fit=crop&w=400&q=80'
]

// Available Options for Dynamic Tags
const availableLanguages = ['English', 'Spanish', 'French', 'Vietnamese', 'Japanese', 'German', 'Italian']
const availableTravelStyles = ['Backpacker', 'Foodie', 'Luxury', 'Adventure', 'Culture', 'Family', 'Solo Travel']
const availableSpecialties = ['Food & Drinks', 'History & Walking', 'Adventure & Outdoor', 'Nightlife', 'Photography', 'Art & Culture']
const countries = ['Vietnam', 'Spain', 'Japan', 'Italy', 'France', 'United States', 'Mexico', 'Thailand', 'South Africa']

// Dynamic Tag Toggles
const toggleLanguage = (lang) => {
  const index = profile.value.languages.indexOf(lang)
  if (index === -1) {
    profile.value.languages.push(lang)
  } else {
    profile.value.languages.splice(index, 1)
  }
}

const toggleTravelStyle = (style) => {
  const index = profile.value.traveller.travelStyles.indexOf(style)
  if (index === -1) {
    profile.value.traveller.travelStyles.push(style)
  } else {
    profile.value.traveller.travelStyles.splice(index, 1)
  }
}

const toggleSpecialty = (spec) => {
  const index = profile.value.guide.specialties.indexOf(spec)
  if (index === -1) {
    profile.value.guide.specialties.push(spec)
  } else {
    profile.value.guide.specialties.splice(index, 1)
  }
}

// Onboarding Completion
const handleFinishOnboarding = () => {
  alert(`Welcome aboard, ${profile.value.fullName}! Your ${accountType.value.toUpperCase()} profile is ready.`)
}
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen text-zinc-900">
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-10">
      
      <!-- Top Title Header -->
      <div class="max-w-3xl space-y-3 text-left">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
          Step 2 of 2 • Setup Profile
        </div>
        <h1 class="text-3xl sm:text-4xl lg:text-5xl font-black tracking-tight leading-[1.15]">
          Welcome! Let's tailor your experience.
        </h1>
        <p class="text-base sm:text-lg text-zinc-600 font-medium leading-relaxed">
          Tell the community who you are. Switch between Traveller or Local Guide at any time.
        </p>
      </div>

      <!-- Main Layout Grid -->
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-8 items-start">
        
        <!-- Left Column: Interactive Form -->
        <div class="lg:col-span-7 space-y-8">
          
          <!-- Section 1: Role Selector -->
          <div class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="text-xs font-bold uppercase tracking-wider text-zinc-400">Choose Your Primary Role</h2>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <!-- Traveller Option Card -->
              <button 
                type="button"
                @click="accountType = 'traveller'"
                class="p-5 rounded-2xl border-2 text-left transition-all duration-200 flex flex-col justify-between gap-4"
                :class="accountType === 'traveller' 
                  ? 'border-emerald-600 bg-emerald-50/40 ring-1 ring-emerald-600/30' 
                  : 'border-zinc-200/80 hover:border-zinc-300 bg-stone-50/50'"
              >
                <div class="flex items-center justify-between">
                  <div class="w-10 h-10 rounded-xl bg-amber-100 text-amber-800 flex items-center justify-center font-bold text-lg">🧳</div>
                  <span v-if="accountType === 'traveller'" class="w-5 h-5 rounded-full bg-emerald-600 text-white flex items-center justify-center text-xs font-bold">✓</span>
                </div>
                <div>
                  <h3 class="text-base font-bold text-zinc-900">I'm a Traveller</h3>
                  <p class="text-xs text-zinc-500 font-medium mt-1">Discover hidden spots, book local guides, and build authentic itineraries.</p>
                </div>
              </button>

              <!-- Local Guide Option Card -->
              <button 
                type="button"
                @click="accountType = 'guide'"
                class="p-5 rounded-2xl border-2 text-left transition-all duration-200 flex flex-col justify-between gap-4"
                :class="accountType === 'guide' 
                  ? 'border-emerald-600 bg-emerald-50/40 ring-1 ring-emerald-600/30' 
                  : 'border-zinc-200/80 hover:border-zinc-300 bg-stone-50/50'"
              >
                <div class="flex items-center justify-between">
                  <div class="w-10 h-10 rounded-xl bg-emerald-100 text-emerald-800 flex items-center justify-center font-bold text-lg">🗺️</div>
                  <span v-if="accountType === 'guide'" class="w-5 h-5 rounded-full bg-emerald-600 text-white flex items-center justify-center text-xs font-bold">✓</span>
                </div>
                <div>
                  <h3 class="text-base font-bold text-zinc-900">I'm a Local Guide</h3>
                  <p class="text-xs text-zinc-500 font-medium mt-1">Host tours, showcase your city's secrets, and earn guiding income.</p>
                </div>
              </button>
            </div>
          </div>

          <!-- Section 2: Avatar & Basic Details -->
          <div class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-6">
            <h2 class="text-xs font-bold uppercase tracking-wider text-zinc-400">Basic Information</h2>

            <!-- Avatar Selection -->
            <div class="space-y-3">
              <label class="text-xs font-bold uppercase text-zinc-700">Profile Photo</label>
              <div class="flex items-center gap-4">
                <img :src="profile.avatarUrl" class="w-20 h-20 rounded-2xl object-cover border-2 border-emerald-600 shadow-sm" />
                <div class="space-y-2">
                  <p class="text-xs text-zinc-500 font-medium">Choose a preset or upload your photo:</p>
                  <div class="flex items-center gap-2">
                    <button 
                      v-for="(img, idx) in sampleAvatars" 
                      :key="idx" 
                      @click="profile.avatarUrl = img"
                      class="w-9 h-9 rounded-xl overflow-hidden border transition-all"
                      :class="profile.avatarUrl === img ? 'ring-2 ring-emerald-600 border-emerald-600' : 'border-zinc-200 opacity-70 hover:opacity-100'"
                    >
                      <img :src="img" class="w-full h-full object-cover" />
                    </button>
                  </div>
                </div>
              </div>
            </div>

            <!-- Full Name & Username -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div class="space-y-1.5">
                <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Full Name</label>
                <input 
                  v-model="profile.fullName" 
                  type="text" 
                  class="w-full px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600"
                />
              </div>

              <div class="space-y-1.5">
                <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Username</label>
                <div class="relative flex items-center px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600">
                  <span class="text-xs font-bold text-zinc-400 mr-1">@</span>
                  <input 
                    v-model="profile.username" 
                    type="text" 
                    class="w-full bg-transparent text-sm font-semibold text-zinc-900 focus:outline-none"
                  />
                </div>
              </div>
            </div>

            <!-- Country & City -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div class="space-y-1.5">
                <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Home Country</label>
                <select v-model="profile.country" class="w-full px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600 cursor-pointer">
                  <option v-for="c in countries" :key="c" :value="c">{{ c }}</option>
                </select>
              </div>

              <div v-if="accountType === 'guide'" class="space-y-1.5">
                <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Primary Guiding City</label>
                <input 
                  v-model="profile.guide.city" 
                  type="text" 
                  placeholder="e.g. Barcelona, Tokyo"
                  class="w-full px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600"
                />
              </div>
            </div>

            <!-- Bio -->
            <div class="space-y-1.5">
              <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Short Bio</label>
              <textarea 
                v-model="profile.bio" 
                rows="3" 
                placeholder="Share a sentence about yourself..."
                class="w-full p-3.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-medium text-zinc-800 focus:outline-none focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600"
              ></textarea>
            </div>

            <!-- Languages Spoken -->
            <div class="space-y-2">
              <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Languages You Speak</label>
              <div class="flex flex-wrap gap-2">
                <button 
                  v-for="lang in availableLanguages" 
                  :key="lang"
                  type="button"
                  @click="toggleLanguage(lang)"
                  class="px-3 py-1.5 rounded-xl text-xs font-bold transition-all"
                  :class="profile.languages.includes(lang) 
                    ? 'bg-zinc-900 text-white shadow-sm' 
                    : 'bg-stone-100 text-zinc-600 hover:bg-stone-200'"
                >
                  {{ lang }} {{ profile.languages.includes(lang) ? '✓' : '+' }}
                </button>
              </div>
            </div>

          </div>

          <!-- Section 3: Dynamic Role-Specific Fields -->
          
          <!-- TRAVELLER SPECIFIC FIELDS -->
          <div v-if="accountType === 'traveller'" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-6">
            <h2 class="text-xs font-bold uppercase tracking-wider text-emerald-600">Traveller Preferences</h2>

            <div class="space-y-2">
              <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Your Preferred Travel Styles</label>
              <div class="flex flex-wrap gap-2">
                <button 
                  v-for="style in availableTravelStyles" 
                  :key="style"
                  type="button"
                  @click="toggleTravelStyle(style)"
                  class="px-3 py-1.5 rounded-xl text-xs font-bold transition-all"
                  :class="profile.traveller.travelStyles.includes(style) 
                    ? 'bg-emerald-600 text-white shadow-sm' 
                    : 'bg-stone-100 text-zinc-600 hover:bg-stone-200'"
                >
                  {{ style }} {{ profile.traveller.travelStyles.includes(style) ? '✓' : '+' }}
                </button>
              </div>
            </div>

            <div class="space-y-1.5">
              <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Preferred Display Currency</label>
              <select v-model="profile.traveller.currency" class="w-full px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600 cursor-pointer">
                <option value="USD">USD ($)</option>
                <option value="EUR">EUR (€)</option>
                <option value="GBP">GBP (£)</option>
                <option value="JPY">JPY (¥)</option>
              </select>
            </div>
          </div>

          <!-- GUIDE SPECIFIC FIELDS -->
          <div v-if="accountType === 'guide'" class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-6">
            <h2 class="text-xs font-bold uppercase tracking-wider text-emerald-600">Guide Hosting Details</h2>

            <!-- Specialties -->
            <div class="space-y-2">
              <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Tour Specialties</label>
              <div class="flex flex-wrap gap-2">
                <button 
                  v-for="spec in availableSpecialties" 
                  :key="spec"
                  type="button"
                  @click="toggleSpecialty(spec)"
                  class="px-3 py-1.5 rounded-xl text-xs font-bold transition-all"
                  :class="profile.guide.specialties.includes(spec) 
                    ? 'bg-emerald-600 text-white shadow-sm' 
                    : 'bg-stone-100 text-zinc-600 hover:bg-stone-200'"
                >
                  {{ spec }} {{ profile.guide.specialties.includes(spec) ? '✓' : '+' }}
                </button>
              </div>
            </div>

            <!-- Rate & Experience -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div class="space-y-1.5">
                <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Base Hourly Rate ($ USD)</label>
                <input 
                  v-model="profile.guide.hourlyRate" 
                  type="number" 
                  class="w-full px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600"
                />
              </div>

              <div class="space-y-1.5">
                <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Guiding Experience</label>
                <select v-model="profile.guide.yearsExperience" class="w-full px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600 cursor-pointer">
                  <option value="1-2 years">1-2 years</option>
                  <option value="3-5 years">3-5 years</option>
                  <option value="5+ years">5+ years local native</option>
                </select>
              </div>
            </div>

            <!-- Intro Video Link -->
            <div class="space-y-1.5">
              <label class="text-xs font-bold uppercase tracking-wider text-zinc-700">Guide Welcome Video URL (Optional)</label>
              <input 
                v-model="profile.guide.introVideoUrl" 
                type="url" 
                placeholder="https://youtube.com/... or Vimeo link"
                class="w-full px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600"
              />
            </div>
          </div>

          <!-- Section 4: Social Links -->
          <div class="bg-white p-6 sm:p-8 rounded-3xl border border-zinc-200/80 shadow-md space-y-4">
            <h2 class="text-xs font-bold uppercase tracking-wider text-zinc-400">Social Media & Web</h2>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div class="space-y-1">
                <label class="text-xs font-bold text-zinc-700">Instagram Handle</label>
                <input 
                  v-model="profile.socials.instagram" 
                  type="text" 
                  placeholder="@username" 
                  class="w-full px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600"
                />
              </div>

              <div class="space-y-1">
                <label class="text-xs font-bold text-zinc-700">Personal Website</label>
                <input 
                  v-model="profile.socials.website" 
                  type="url" 
                  placeholder="https://..." 
                  class="w-full px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 text-sm font-semibold text-zinc-900 focus:outline-none focus:border-emerald-600"
                />
              </div>
            </div>
          </div>

          <!-- Submit Button -->
          <button 
            @click="handleFinishOnboarding"
            class="w-full py-4 bg-zinc-900 hover:bg-emerald-600 text-white font-bold text-base rounded-2xl shadow-xl hover:shadow-emerald-600/20 transition-all duration-200 flex items-center justify-center gap-2 group"
          >
            <span>Complete Profile & Start Exploring</span>
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-5 h-5 group-hover:translate-x-1 transition-transform">
              <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
            </svg>
          </button>

        </div>

        <!-- Right Column: Live Profile Preview Card -->
        <div class="lg:col-span-5 relative lg:sticky lg:top-8 space-y-4">
          <div class="flex items-center justify-between px-2">
            <p class="text-xs font-bold uppercase tracking-wider text-zinc-400">Live Profile Preview</p>
            <span class="text-xs font-bold text-emerald-700 bg-emerald-100 px-2.5 py-0.5 rounded-full uppercase">Realtime</span>
          </div>

          <div class="bg-white p-6 rounded-3xl border border-zinc-200/80 shadow-xl space-y-6">
            
            <!-- Card Header -->
            <div class="flex items-start gap-4">
              <div class="relative">
                <img :src="profile.avatarUrl" class="w-16 h-16 rounded-2xl object-cover border border-zinc-200 shadow-sm" />
                <span 
                  class="absolute -bottom-1 -right-1 w-5 h-5 rounded-full border-2 border-white flex items-center justify-center text-[10px] text-white font-bold"
                  :class="accountType === 'guide' ? 'bg-emerald-500' : 'bg-amber-500'"
                >
                  ✓
                </span>
              </div>

              <div>
                <div class="flex items-center gap-2">
                  <h3 class="text-lg font-bold text-zinc-900">{{ profile.fullName || 'Your Name' }}</h3>
                </div>
                <p class="text-xs text-zinc-400 font-medium">@{{ profile.username || 'username' }}</p>
                <div class="inline-flex items-center gap-1.5 mt-1.5 px-2.5 py-0.5 rounded-md bg-stone-100 text-xs font-bold text-zinc-700">
                  <span>{{ accountType === 'guide' ? '🗺️ Local Guide' : '🧳 Traveller' }}</span>
                  <span>•</span>
                  <span>{{ profile.country }}</span>
                </div>
              </div>
            </div>

            <!-- Bio Preview -->
            <p class="text-xs text-zinc-600 font-medium leading-relaxed bg-stone-50 p-3 rounded-xl border border-zinc-100">
              "{{ profile.bio || 'Your bio will show up here...' }}"
            </p>

            <!-- Guide Specific Rate & City Badge -->
            <div v-if="accountType === 'guide'" class="p-4 bg-emerald-50/60 rounded-2xl border border-emerald-200/70 flex items-center justify-between">
              <div>
                <p class="text-[11px] font-bold text-emerald-800 uppercase">Guiding Location</p>
                <p class="text-sm font-bold text-zinc-900">{{ profile.guide.city || 'Set City' }}</p>
              </div>
              <div class="text-right">
                <p class="text-[11px] font-bold text-emerald-800 uppercase">Rate</p>
                <p class="text-sm font-black text-zinc-900">${{ profile.guide.hourlyRate }}/hr</p>
              </div>
            </div>

            <!-- Languages -->
            <div class="space-y-1.5">
              <p class="text-[11px] font-bold uppercase tracking-wider text-zinc-400">Languages</p>
              <div class="flex flex-wrap gap-1.5">
                <span v-for="l in profile.languages" :key="l" class="px-2.5 py-1 rounded-lg bg-stone-100 text-zinc-700 text-xs font-semibold">
                  {{ l }}
                </span>
              </div>
            </div>

            <!-- Dynamic Tags Preview -->
            <div class="space-y-1.5">
              <p class="text-[11px] font-bold uppercase tracking-wider text-zinc-400">
                {{ accountType === 'guide' ? 'Guiding Specialties' : 'Travel Styles' }}
              </p>
              <div class="flex flex-wrap gap-1.5">
                <template v-if="accountType === 'traveller'">
                  <span v-for="st in profile.traveller.travelStyles" :key="st" class="px-2.5 py-1 rounded-lg bg-amber-100/80 text-amber-900 text-xs font-bold">
                    {{ st }}
                  </span>
                </template>
                <template v-else>
                  <span v-for="sp in profile.guide.specialties" :key="sp" class="px-2.5 py-1 rounded-lg bg-emerald-100 text-emerald-900 text-xs font-bold">
                    {{ sp }}
                  </span>
                </template>
              </div>
            </div>

            <!-- Social Links Preview -->
            <div v-if="profile.socials.instagram || profile.socials.website" class="pt-2 border-t border-zinc-100 flex items-center gap-3 text-xs text-zinc-500 font-medium">
              <span v-if="profile.socials.instagram">📸 @{{ profile.socials.instagram }}</span>
              <span v-if="profile.socials.website">🌐 Website</span>
            </div>

          </div>
        </div>

      </div>

    </div>
  </section>
</template>