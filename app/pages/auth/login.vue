<script setup>
import { ref } from 'vue'

const email = ref('')
const password = ref('')
const rememberMe = ref(false)
const showPassword = ref(false)

const handleLogin = () => {
  console.log('Authenticating user:', { email: email.value, password: password.value, rememberMe: rememberMe.value })
}

const handleGoogleLogin = () => {
  console.log('Initiating Google OAuth flow...')
}
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-[85vh] flex items-center">
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 w-full">
      <div class="max-w-md mx-auto">
        
        <!-- Header Copy -->
        <div class="text-center mb-8 space-y-3">
          <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider">
            <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
            Welcome Back
          </div>
          
          <h1 class="text-3xl sm:text-4xl font-black text-zinc-900 tracking-tight">
            Log in to <span class="text-emerald-600">Leeto</span>
          </h1>
          
          <p class="text-sm text-zinc-600 font-medium">
            Access your bookings, saved guides, and custom travel itineraries.
          </p>
        </div>

        <!-- Login Card Container -->
        <div class="bg-white p-6 sm:p-8 rounded-3xl shadow-xl shadow-zinc-200/60 border border-zinc-200/80">
          
          <!-- Google OAuth Action -->
          <button 
            @click="handleGoogleLogin"
            type="button"
            class="w-full py-3 px-4 bg-white hover:bg-stone-50 text-zinc-800 font-bold text-sm rounded-xl border border-zinc-200/80 shadow-sm transition-all duration-200 flex items-center justify-center gap-3 active:scale-95 cursor-pointer mb-6"
          >
            <svg class="w-5 h-5 shrink-0" viewBox="0 0 24 24">
              <path fill="#4285F4" d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"/>
              <path fill="#34A853" d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"/>
              <path fill="#FBBC05" d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.06H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.94l2.85-2.22.81-.63z"/>
              <path fill="#EA4335" d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.06l3.66 2.84c.87-2.6 3.3-4.52 6.16-4.52z"/>
            </svg>
            <span>Continue with Google</span>
          </button>

          <!-- Visual Divider -->
          <div class="relative flex items-center justify-center my-6">
            <div class="border-t border-zinc-200/80 w-full"></div>
            <span class="bg-white px-3 text-[11px] uppercase text-zinc-400 font-bold tracking-wider absolute">Or continue with email</span>
          </div>

          <!-- Direct Form Sign-In -->
          <form @submit.prevent="handleLogin" class="space-y-4">
            
            <!-- Email Input -->
            <div class="space-y-1.5">
              <label class="block text-xs font-bold uppercase tracking-wider text-zinc-700">Email Address</label>
              <div class="relative flex items-center px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5 text-zinc-400 shrink-0 mr-2.5">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" />
                </svg>
                <input 
                  v-model="email"
                  type="email" 
                  required
                  placeholder="you@example.com"
                  class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-semibold focus:outline-none"
                />
              </div>
            </div>

            <!-- Password Input -->
            <div class="space-y-1.5">
              <div class="flex items-center justify-between">
                <label class="block text-xs font-bold uppercase tracking-wider text-zinc-700">Password</label>
                <a href="#forgot-password" class="text-xs font-semibold text-emerald-600 hover:text-emerald-700 transition-colors">Forgot?</a>
              </div>
              <div class="relative flex items-center px-3.5 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5 text-zinc-400 shrink-0 mr-2.5">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M16.5 10.5V6.75a4.5 4.5 0 10-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 002.25-2.25v-6.75a2.25 2.25 0 00-2.25-2.25H6.75a2.25 2.25 0 00-2.25 2.25v6.75a2.25 2.25 0 002.25 2.25z" />
                </svg>
                <input 
                  v-model="password"
                  :type="showPassword ? 'text' : 'password'"
                  required
                  placeholder="••••••••"
                  class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-semibold focus:outline-none"
                />
                <button 
                  type="button" 
                  @click="showPassword = !showPassword"
                  class="text-zinc-400 hover:text-zinc-600 text-xs font-bold transition-colors ml-2 shrink-0 cursor-pointer"
                >
                  {{ showPassword ? 'Hide' : 'Show' }}
                </button>
              </div>
            </div>

            <!-- Remember Me Control -->
            <div class="flex items-center justify-between pt-1">
              <label class="flex items-center gap-2 cursor-pointer select-none">
                <input 
                  v-model="rememberMe"
                  type="checkbox" 
                  class="w-4 h-4 rounded border-zinc-300 text-emerald-600 focus:ring-emerald-500 cursor-pointer"
                />
                <span class="text-xs font-semibold text-zinc-600">Keep me signed in</span>
              </label>
            </div>

            <!-- Submit Button -->
            <button 
              type="submit" 
              class="w-full py-3.5 px-6 bg-zinc-900 hover:bg-emerald-600 text-white font-bold text-sm rounded-xl shadow-md hover:shadow-emerald-600/20 transition-all duration-200 active:scale-95 cursor-pointer mt-2"
            >
              Sign In
            </button>
          </form>

          <!-- Sign Up Switcher -->
          <div class="mt-6 pt-5 border-t border-zinc-100 text-center">
            <p class="text-xs text-zinc-500 font-medium">
              Don't have an account yet? 
              <a href="#signup" class="font-bold text-emerald-600 hover:text-emerald-700 transition-colors">
                Create an account
              </a>
            </p>
          </div>

        </div>

      </div>
    </div>
  </section>
</template>