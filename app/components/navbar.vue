<script setup>
import { ref } from 'vue'

const isMobileMenuOpen = ref(false)
</script>

<template>
  <header class="sticky top-0 z-50 bg-stone-50/90 backdrop-blur-md border-b border-zinc-200/80 text-zinc-600 font-sans transition-all duration-200">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-20">
        
        <!-- Brand / Logo -->
        <NuxtLink to="/" class="flex items-center gap-3 group">
          <div class="w-10 h-10 rounded-xl bg-emerald-600 flex items-center justify-center text-white shadow-md group-hover:bg-zinc-900 transition-colors duration-300">
            <!-- Travel Compass/Pin Icon -->
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9 9 0 100-18 9 9 0 000 18z" />
              <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 13.5l3-4.5-1.5 6 4.5-3-6 1.5z" />
            </svg>
          </div>
          <span class="text-2xl font-black text-zinc-900 tracking-tight">Leeto</span>
        </NuxtLink>

        <!-- Desktop Navigation Links -->
        <nav class="hidden md:flex items-center space-x-8 text-sm font-semibold">
          <NuxtLink 
            to="/guides" 
            class="text-zinc-700 hover:text-emerald-600 transition-colors flex items-center gap-1.5"
          >
            Find a Guide
          </NuxtLink>
          <NuxtLink 
            to="/destinations" 
            class="text-zinc-700 hover:text-emerald-600 transition-colors"
          >
            Destinations
          </NuxtLink>
          <NuxtLink 
            to="/become-a-guide" 
            class="text-zinc-700 hover:text-emerald-600 transition-colors flex items-center gap-1.5"
          >
            Become a Guide
            <span class="px-2 py-0.5 text-[10px] bg-amber-100 text-amber-800 rounded-full font-bold uppercase tracking-wider">Earn</span>
          </NuxtLink>
          <NuxtLink 
            to="/how-it-works" 
            class="text-zinc-700 hover:text-emerald-600 transition-colors"
          >
            How It Works
          </NuxtLink>
        </nav>

        <!-- Action Buttons -->
        <div class="hidden md:flex items-center gap-3">
          <NuxtLink 
            to="/auth/login" 
            class="text-sm font-semibold text-zinc-700 hover:text-emerald-600 px-4 py-2.5 transition-colors"
          >
            Sign In
          </NuxtLink>
          <NuxtLink 
            to="/auth/register" 
            class="inline-flex items-center gap-2 bg-zinc-900 hover:bg-emerald-600 text-white font-semibold text-sm px-5 py-2.5 rounded-xl shadow-md hover:shadow-emerald-600/20 transition-all duration-200"
          >
            Explore Tours
            <svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" class="w-4 h-4" viewBox="0 0 24 24">
              <path d="M5 12h14M12 5l7 7-7 7"></path>
            </svg>
          </NuxtLink>
        </div>

        <!-- Mobile Menu Toggle Button -->
        <div class="flex md:hidden items-center">
          <button 
            @click="isMobileMenuOpen = !isMobileMenuOpen"
            type="button" 
            class="p-2 rounded-xl text-zinc-700 hover:bg-zinc-200/60 focus:outline-none"
            aria-label="Toggle menu"
          >
            <svg v-if="!isMobileMenuOpen" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
            </svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>

      </div>
    </div>

    <!-- Mobile Dropdown Navigation -->
    <div 
      v-show="isMobileMenuOpen" 
      class="md:hidden border-t border-zinc-200/80 bg-stone-50 px-4 pt-3 pb-6 space-y-3 shadow-lg"
    >
      <NuxtLink 
        to="/guides" 
        class="block px-3 py-2.5 rounded-lg text-base font-medium text-zinc-800 hover:bg-zinc-200/50"
      >
        Find a Guide 🧭
      </NuxtLink>
      <NuxtLink 
        to="/destinations" 
        class="block px-3 py-2.5 rounded-lg text-base font-medium text-zinc-800 hover:bg-zinc-200/50"
      >
        Destinations 📍
      </NuxtLink>
      <NuxtLink 
        to="/become-a-guide" 
        class="block px-3 py-2.5 rounded-lg text-base font-medium text-zinc-800 hover:bg-zinc-200/50"
      >
        Become a Guide 💵
      </NuxtLink>
      <NuxtLink 
        to="/how-it-works" 
        class="block px-3 py-2.5 rounded-lg text-base font-medium text-zinc-800 hover:bg-zinc-200/50"
      >
        How It Works
      </NuxtLink>

      <div class="pt-4 border-t border-zinc-200/80 flex flex-col gap-2">
        <NuxtLink 
          to="/auth/login" 
          class="w-full text-center px-4 py-2.5 rounded-xl text-sm font-semibold text-zinc-800 bg-zinc-200/60 hover:bg-zinc-200"
        >
          Sign In
        </NuxtLink>
        <NuxtLink 
          to="/auth/register" 
          class="w-full text-center px-4 py-2.5 rounded-xl text-sm font-semibold text-white bg-zinc-900 hover:bg-emerald-600 shadow-md transition-colors"
        >
          Explore Tours
        </NuxtLink>
      </div>
    </div>
  </header>
</template>