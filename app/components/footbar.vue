<script setup>
import { ref } from 'vue'

const email = ref('')

const handleSubscribe = () => {
  if (email.value) {
    console.log(`Subscribed with: ${email.value}`)
    email.value = ''
  }
}
</script>

<template>
  <footer class="bg-stone-50 border-t border-zinc-200/80 text-zinc-600 font-sans">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 pt-16 pb-12">
      
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-10 lg:gap-8 pb-12 border-b border-zinc-200/80">
        
        <div class="lg:col-span-2 space-y-4">
          <NuxtLink to="/" class="flex items-center gap-3 group">
            <div class="w-10 h-10 rounded-xl bg-emerald-600 flex items-center justify-center text-white shadow-md group-hover:bg-zinc-900 transition-colors duration-300">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9 9 0 100-18 9 9 0 000 18z" />
                <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 13.5l3-4.5-1.5 6 4.5-3-6 1.5z" />
              </svg>
            </div>
            <span class="text-2xl font-black font-heading text-zinc-900 tracking-tight">Leeto</span>
          </NuxtLink>
          <p class="text-sm text-zinc-600 max-w-sm leading-relaxed font-sans">
            Connecting travelers with passionate local guides worldwide. Experience authentic stories, hidden spots, and unforgettable private tours.
          </p>

          <div class="pt-2 max-w-sm">
            <span class="text-xs font-bold font-heading uppercase tracking-wider text-zinc-400 block mb-2">Subscribe to trip inspiration</span>
            <form @submit.prevent="handleSubscribe" class="flex gap-2">
              <input 
                v-model="email"
                type="email" 
                placeholder="Enter your email" 
                required
                class="w-full bg-white border border-zinc-200 rounded-xl px-3.5 py-2 text-sm text-zinc-900 font-sans focus:outline-none focus:border-emerald-600 placeholder-zinc-400"
              />
              <button 
                type="submit" 
                class="bg-zinc-900 hover:bg-emerald-600 text-white font-heading font-bold text-sm px-4 py-2 rounded-xl transition-colors shrink-0"
              >
                Join
              </button>
            </form>
          </div>
        </div>

        <div class="space-y-3">
          <p class="text-xs font-bold font-heading uppercase tracking-wider text-zinc-900">Discover</p>
          <ul class="space-y-2.5 text-sm font-medium font-sans">
            <li>
              <NuxtLink to="/guides" class="hover:text-emerald-600 transition-colors">Find Local Guides</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/destinations" class="hover:text-emerald-600 transition-colors">Popular Cities</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/categories/food" class="hover:text-emerald-600 transition-colors">Food & Culinary</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/categories/culture" class="hover:text-emerald-600 transition-colors">Culture & Heritage</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/gift-cards" class="hover:text-emerald-600 transition-colors">Gift Cards</NuxtLink>
            </li>
          </ul>
        </div>

        <div class="space-y-3">
          <p class="text-xs font-bold font-heading uppercase tracking-wider text-zinc-900">For Guides</p>
          <ul class="space-y-2.5 text-sm font-medium font-sans">
            <li>
              <NuxtLink to="/become-a-guide" class="hover:text-emerald-600 transition-colors flex items-center gap-1.5">
                Become a Guide
                <span class="px-1.5 py-0.5 text-[9px] bg-amber-100 text-amber-800 rounded font-bold uppercase font-heading">Earn</span>
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/guide-stories" class="hover:text-emerald-600 transition-colors">Host Stories</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/community" class="hover:text-emerald-600 transition-colors">Guide Community</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/safety" class="hover:text-emerald-600 transition-colors">Host Guarantee</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/resources" class="hover:text-emerald-600 transition-colors">Resource Hub</NuxtLink>
            </li>
          </ul>
        </div>

        <div class="space-y-3">
          <p class="text-xs font-bold font-heading uppercase tracking-wider text-zinc-900">Company</p>
          <ul class="space-y-2.5 text-sm font-medium font-sans">
            <li>
              <NuxtLink to="/about" class="hover:text-emerald-600 transition-colors">About Us</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/careers" class="hover:text-emerald-600 transition-colors flex items-center gap-1">
                Careers
                <span class="w-1.5 h-1.5 rounded-full bg-emerald-600"></span>
              </NuxtLink>
            </li>
            <li>
              <NuxtLink to="/help" class="hover:text-emerald-600 transition-colors">Help Center</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/press" class="hover:text-emerald-600 transition-colors">Press</NuxtLink>
            </li>
            <li>
              <NuxtLink to="/contact" class="hover:text-emerald-600 transition-colors">Contact Support</NuxtLink>
            </li>
          </ul>
        </div>

      </div>

      <div class="pt-8 flex flex-col md:flex-row items-center justify-between gap-4 text-xs font-medium font-sans text-zinc-500">
        
        <div class="flex flex-wrap items-center justify-center md:justify-start gap-4 sm:gap-6">
          <p>© {{ new Date().getFullYear() }} Leeto, Inc. All rights reserved.</p>
          <NuxtLink to="/privacy" class="hover:text-zinc-900 transition-colors">Privacy Policy</NuxtLink>
          <NuxtLink to="/terms" class="hover:text-zinc-900 transition-colors">Terms of Service</NuxtLink>
          <NuxtLink to="/cookies" class="hover:text-zinc-900 transition-colors">Cookie Settings</NuxtLink>
        </div>

        <div class="flex items-center gap-4 text-zinc-600">
          <a href="#" aria-label="Instagram" class="hover:text-emerald-600 transition-colors p-1">
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
          </a>
          <a href="#" aria-label="Twitter / X" class="hover:text-emerald-600 transition-colors p-1">
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
          </a>
          <a href="#" aria-label="Facebook" class="hover:text-emerald-600 transition-colors p-1">
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>
          </a>
        </div>

      </div>

    </div>
  </footer>
</template>