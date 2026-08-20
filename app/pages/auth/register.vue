<script setup>
import { ref } from 'vue'

const firstName = ref('')
const lastName = ref('')
const email = ref('')
const password = ref('')
const accountType = ref('traveler') // 'traveler' or 'guide'
const showPassword = ref(false)

const handleRegister = () => {
  console.log('Registering user:', {
    firstName: firstName.value,
    lastName: lastName.value,
    email: email.value,
    password: password.value,
    accountType: accountType.value
  })
}

const handleGoogleLogin = () => {
  console.log('Initiating Google Auth...')
}
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen flex items-center">
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 w-full">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-8 items-center">
        
        <!-- Copy & Value Proposition (Left) -->
        <div class="lg:col-span-7 space-y-8 text-center lg:text-left">
          
          <!-- Badge -->
          <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-emerald-100/80 border border-emerald-200/70 text-emerald-900 text-xs font-bold uppercase tracking-wider">
            <span class="flex h-2 w-2 rounded-full bg-emerald-500"></span>
            Join the Leeto Community
          </div>

          <!-- Main Heading -->
          <h1 class="text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
            Start exploring cities with people who <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">live there.</span>
          </h1>

          <!-- Description -->
          <p class="text-base sm:text-lg text-zinc-600 max-w-2xl mx-auto lg:mx-0 font-medium leading-relaxed">
            Create an account to book personalized local tours, message verified guides directly, and unlock secret spots off the tourist grid.
          </p>

          <!-- Feature Highlights List -->
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 max-w-xl mx-auto lg:mx-0 text-left pt-2">
            <div class="flex items-start gap-3 p-3 rounded-2xl bg-white/60 border border-zinc-200/50 backdrop-blur-sm">
              <div class="w-8 h-8 rounded-xl bg-amber-100 text-amber-800 flex items-center justify-center font-bold shrink-0">
                🗺️
              </div>
              <div>
                <h4 class="text-xs font-bold text-zinc-900">100% Custom Tours</h4>
                <p class="text-[11px] text-zinc-500">Tailor itineraries to your schedule</p>
              </div>
            </div>

            <div class="flex items-start gap-3 p-3 rounded-2xl bg-white/60 border border-zinc-200/50 backdrop-blur-sm">
              <div class="w-8 h-8 rounded-xl bg-emerald-100 text-emerald-800 flex items-center justify-center font-bold shrink-0">
                🔒
              </div>
              <div>
                <h4 class="text-xs font-bold text-zinc-900">Verified Hosts</h4>
                <p class="text-[11px] text-zinc-500">Identity checked & peer-reviewed</p>
              </div>
            </div>
          </div>

          <!-- Quick Login Redirect -->
          <p class="text-xs sm:text-sm text-zinc-500 pt-2">
            Already have a Leeto account? 
            <a href="#login" class="font-bold text-emerald-600 hover:text-emerald-700 underline underline-offset-2">Log in here</a>
          </p>

        </div>

        <!-- Registration Form Card (Right) -->
        <div class="lg:col-span-5 relative">
          <div class="relative bg-white p-6 sm:p-8 rounded-3xl shadow-2xl border border-zinc-200/80">
            
            <div class="mb-6 text-center lg:text-left">
              <h2 class="text-2xl font-black text-zinc-900 tracking-tight">Create your account</h2>
              <p class="text-xs text-zinc-500 mt-1 font-medium">Join in seconds to start discovering or guiding</p>
            </div>

            <!-- User Type Selector -->
            <div class="grid grid-cols-2 gap-1.5 p-1 bg-stone-100 rounded-xl mb-6 text-xs font-bold">
              <button 
                type="button"
                @click="accountType = 'traveler'"
                :class="accountType === 'traveler' ? 'bg-white text-zinc-900 shadow-sm' : 'text-zinc-500 hover:text-zinc-900'"
                class="py-2 rounded-lg transition-all text-center cursor-pointer"
              >
                🧳 I'm a Traveler
              </button>
              <button 
                type="button"
                @click="accountType = 'guide'"
                :class="accountType === 'guide' ? 'bg-white text-zinc-900 shadow-sm' : 'text-zinc-500 hover:text-zinc-900'"
                class="py-2 rounded-lg transition-all text-center cursor-pointer"
              >
                🚩 I'm a Local Guide
              </button>
            </div>

            <!-- Google OAuth Button -->
            <button 
              @click="handleGoogleLogin"
              type="button"
              class="w-full py-3 px-4 bg-white hover:bg-stone-50 text-zinc-700 font-bold text-sm rounded-xl border border-zinc-200/90 shadow-sm transition-all duration-150 flex items-center justify-center gap-3 active:scale-[0.99] cursor-pointer mb-5"
            >
              <svg class="w-5 h-5 shrink-0" viewBox="0 0 24 24">
                <path fill="#4285F4" d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"/>
                <path fill="#34A853" d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"/>
                <path fill="#FBBC05" d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.06H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.94l2.85-2.22.81-.63z"/>
                <path fill="#EA4335" d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.06l3.66 2.84c.87-2.6 3.3-4.52 6.16-4.52z"/>
              </svg>
              <span>Continue with Google</span>
            </button>

            <!-- Divider -->
            <div class="relative flex items-center justify-center mb-5">
              <div class="border-t border-zinc-200/80 w-full"></div>
              <span class="bg-white px-3 text-[11px] font-bold uppercase tracking-wider text-zinc-400 absolute">or email</span>
            </div>

            <!-- Form -->
            <form @submit.prevent="handleRegister" class="space-y-4">
              
              <!-- First & Last Name Row -->
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
                <div class="space-y-1">
                  <label class="text-xs font-bold text-zinc-700">First Name</label>
                  <div class="relative flex items-center px-3 py-2 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                    <input 
                      v-model="firstName"
                      type="text" 
                      required
                      placeholder="Jane" 
                      class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-medium focus:outline-none"
                    />
                  </div>
                </div>

                <div class="space-y-1">
                  <label class="text-xs font-bold text-zinc-700">Last Name</label>
                  <div class="relative flex items-center px-3 py-2 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                    <input 
                      v-model="lastName"
                      type="text" 
                      required
                      placeholder="Doe" 
                      class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-medium focus:outline-none"
                    />
                  </div>
                </div>
              </div>

              <!-- Email Field -->
              <div class="space-y-1">
                <label class="text-xs font-bold text-zinc-700">Email Address</label>
                <div class="relative flex items-center px-3 py-2 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4 text-zinc-400 shrink-0 mr-2.5">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" />
                  </svg>
                  <input 
                    v-model="email"
                    type="email" 
                    required
                    placeholder="jane@example.com" 
                    class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-medium focus:outline-none"
                  />
                </div>
              </div>

              <!-- Password Field -->
              <div class="space-y-1">
                <label class="text-xs font-bold text-zinc-700">Password</label>
                <div class="relative flex items-center px-3 py-2 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4 text-zinc-400 shrink-0 mr-2.5">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M16.5 10.5V6.75a4.5 4.5 0 10-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 002.25-2.25v-6.75a2.25 2.25 0 00-2.25-2.25H6.75a2.25 2.25 0 00-2.25 2.25v6.75a2.25 2.25 0 002.25 2.25z" />
                  </svg>
                  <input 
                    v-model="password"
                    :type="showPassword ? 'text' : 'password'" 
                    required
                    placeholder="Min. 8 characters" 
                    class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-medium focus:outline-none"
                  />
                  <button 
                    @click="showPassword = !showPassword" 
                    type="button" 
                    class="text-xs font-bold text-zinc-400 hover:text-zinc-700 cursor-pointer focus:outline-none"
                  >
                    {{ showPassword ? 'Hide' : 'Show' }}
                  </button>
                </div>
              </div>

              <!-- Submit Button -->
              <button 
                type="submit" 
                class="w-full py-3.5 px-6 bg-zinc-900 hover:bg-emerald-600 text-white font-bold text-sm rounded-xl shadow-md hover:shadow-emerald-600/20 transition-all duration-200 flex items-center justify-center gap-2 shrink-0 group cursor-pointer active:scale-[0.99] mt-2"
              >
                <span>Create Account</span>
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4 group-hover:translate-x-0.5 transition-transform">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
                </svg>
              </button>

              <!-- Terms Disclaimer -->
              <p class="text-[10px] text-zinc-400 text-center leading-relaxed pt-1">
                By creating an account, you agree to Leeto’s 
                <a href="#terms" class="underline font-semibold hover:text-zinc-600">Terms of Service</a> and 
                <a href="#privacy" class="underline font-semibold hover:text-zinc-600">Privacy Policy</a>.
              </p>

            </form>

          </div>
        </div>

      </div>
    </div>
  </section>
</template>