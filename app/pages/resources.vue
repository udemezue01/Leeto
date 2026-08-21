<script setup>
import { ref, computed } from 'vue'

const selectedCategory = ref('All')
const searchQuery = ref('')

const categories = [
  'All',
  'Local Guides',
  'Hidden Gems',
  'Food & Culture',
  'Travel Tips'
]

const featuredPost = {
  id: 1,
  title: 'Beyond the Canals: 7 Secret Neighborhoods in Venice Only Locals Know',
  excerpt: 'Escape the tourist crowds in St. Mark’s Square and discover quiet artisan workshops, hidden wine bars, and peaceful lagoon views in Venice’s lesser-known districts.',
  category: 'Hidden Gems',
  readTime: '6 min read',
  date: 'August 18, 2026',
  image: 'https://images.unsplash.com/photo-1514890547357-a9ee288728e0?auto=format&fit=crop&w=1200&q=80',
  author: {
    name: 'Elena Rossi',
    role: 'Venetian Local & Art Historian',
    avatar: 'https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=200&q=80'
  }
}

const posts = ref([
  {
    id: 2,
    title: 'How to Eat Like a Local in Tokyo: Etiquette & Izakaya Secrets',
    excerpt: 'Navigating Tokyo’s vast culinary landscape can be daunting. Here is your local guide to ordering, etiquette, and discovering neighborhood izakayas.',
    category: 'Food & Culture',
    readTime: '5 min read',
    date: 'August 14, 2026',
    image: 'https://images.unsplash.com/photo-1503899036084-c55cdd92da26?auto=format&fit=crop&w=800&q=80',
    author: {
      name: 'Kenji Sato',
      role: 'Tokyo Culinary Guide',
      avatar: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&w=150&q=80'
    }
  },
  {
    id: 3,
    title: '5 Sustainable Travel Habits Every Modern Explorer Should Adopt',
    excerpt: 'Small choices make a big impact. Discover practical ways to lower your carbon footprint and support local economies while traveling abroad.',
    category: 'Travel Tips',
    readTime: '4 min read',
    date: 'August 10, 2026',
    image: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=800&q=80',
    author: {
      name: 'Maya Lin',
      role: 'Eco-Tourism Specialist',
      avatar: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?auto=format&fit=crop&w=150&q=80'
    }
  },
  {
    id: 4,
    title: 'A Day in the Life of a Local Guide in Cape Town',
    excerpt: 'Step behind the scenes with Thabo as he leads sunrise mountain hikes, introduces travelers to coastal cuisine, and shares his city’s rich history.',
    category: 'Local Guides',
    readTime: '7 min read',
    date: 'August 05, 2026',
    image: 'https://images.unsplash.com/photo-1580618672591-eb180b1a973f?auto=format&fit=crop&w=800&q=80',
    author: {
      name: 'Thabo Mbeki',
      role: 'Cape Town Native Guide',
      avatar: 'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?auto=format&fit=crop&w=150&q=80'
    }
  },
  {
    id: 5,
    title: 'Exploring Kyoto during Off-Peak Hours: Temples Without Crowds',
    excerpt: 'Kyoto is legendary for its heritage, but peak hours bring dense crowds. Learn the exact times and alternative routes to experience serene gardens.',
    category: 'Hidden Gems',
    readTime: '5 min read',
    date: 'July 29, 2026',
    image: 'https://images.unsplash.com/photo-1493976040374-85c8e12f0c0e?auto=format&fit=crop&w=800&q=80',
    author: {
      name: 'Kenji Sato',
      role: 'Tokyo Culinary Guide',
      avatar: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&w=150&q=80'
    }
  },
  {
    id: 6,
    title: 'Street Food Safety 101: Enjoy Authentic Bites Conflict-Free',
    excerpt: 'Don’t let stomach worries keep you from the best food on earth. Learn how to spot high-turnover stalls and safe drinking practices anywhere.',
    category: 'Food & Culture',
    readTime: '4 min read',
    date: 'July 22, 2026',
    image: 'https://images.unsplash.com/photo-1555396273-367ea4eb4db5?auto=format&fit=crop&w=800&q=80',
    author: {
      name: 'Elena Rossi',
      role: 'Venetian Local & Art Historian',
      avatar: 'https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=200&q=80'
    }
  },
  {
    id: 7,
    title: 'Packing Light for Multi-Climate Tours: The Minimalist Guide',
    excerpt: 'Mastering the art of capsule travel wardrobes. How to pack for freezing mountain tops and tropical beaches in a single carry-on bag.',
    category: 'Travel Tips',
    readTime: '6 min read',
    date: 'July 15, 2026',
    image: 'https://images.unsplash.com/photo-1488646953014-85cb44e25828?auto=format&fit=crop&w=800&q=80',
    author: {
      name: 'Maya Lin',
      role: 'Eco-Tourism Specialist',
      avatar: 'https://images.unsplash.com/photo-1494790108377-be9c29b29330?auto=format&fit=crop&w=150&q=80'
    }
  }
])

const newsletterEmail = ref('')

const filteredPosts = computed(() => {
  return posts.value.filter(post => {
    const matchesCategory = selectedCategory.value === 'All' || post.category === selectedCategory.value
    const matchesSearch = post.title.toLowerCase().includes(searchQuery.value.toLowerCase()) || 
                          post.excerpt.toLowerCase().includes(searchQuery.value.toLowerCase())
    return matchesCategory && matchesSearch
  })
})

const handleSubscribe = () => {
  if (newsletterEmail.value.trim()) {
    alert(`Thank you for subscribing with ${newsletterEmail.value}!`)
    newsletterEmail.value = ''
  }
}
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen text-zinc-900">
    
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-12">

      <div class="text-center max-w-3xl mx-auto space-y-4">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-heading font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
          Stories & Insights
        </div>

        <h1 class="font-heading text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
          Explore the world <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">through local eyes.</span>
        </h1>

        <p class="font-sans text-base sm:text-lg text-zinc-600 font-medium leading-relaxed max-w-2xl mx-auto">
          Insider guides, hidden spots, and authentic travel tips written by local experts worldwide.
        </p>
      </div>

      <div class="bg-white rounded-3xl border border-zinc-200/80 shadow-xl overflow-hidden group">
        <div class="grid grid-cols-1 lg:grid-cols-12 items-center">
          
          <div class="lg:col-span-7 relative h-72 sm:h-96 lg:h-[460px] overflow-hidden bg-zinc-900">
            <img 
              :src="featuredPost.image" 
              :alt="featuredPost.title" 
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500 opacity-90"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-zinc-950/60 via-transparent to-transparent lg:hidden"></div>
            
            <div class="absolute top-4 left-4 bg-zinc-900/80 backdrop-blur-md px-3 py-1.5 rounded-full text-white text-xs font-heading font-bold flex items-center gap-2 border border-white/10">
              <span class="w-2 h-2 rounded-full bg-amber-400"></span>
              Featured Story
            </div>
          </div>

          <div class="lg:col-span-5 p-6 sm:p-8 lg:p-10 space-y-6">
            <div class="flex items-center gap-3 text-xs font-sans font-bold text-zinc-500">
              <span class="px-2.5 py-1 rounded-md bg-stone-100 text-zinc-800 font-heading">{{ featuredPost.category }}</span>
              <span>•</span>
              <span>{{ featuredPost.readTime }}</span>
            </div>

            <h2 class="font-heading text-2xl sm:text-3xl font-black text-zinc-900 tracking-tight leading-snug hover:text-emerald-600 transition-colors cursor-pointer">
              {{ featuredPost.title }}
            </h2>

            <p class="font-sans text-sm text-zinc-600 font-medium leading-relaxed">
              {{ featuredPost.excerpt }}
            </p>

            <div class="pt-4 border-t border-zinc-100 flex items-center justify-between">
              <div class="flex items-center gap-3">
                <img :src="featuredPost.author.avatar" :alt="featuredPost.author.name" class="w-10 h-10 rounded-xl object-cover" />
                <div>
                  <p class="font-heading text-xs font-bold text-zinc-900">{{ featuredPost.author.name }}</p>
                  <p class="font-sans text-[11px] text-zinc-400 font-medium">{{ featuredPost.author.role }}</p>
                </div>
              </div>

              <button class="px-4 py-2 bg-zinc-900 hover:bg-emerald-600 text-white font-sans font-bold text-xs rounded-xl shadow-md transition-all flex items-center gap-1.5 group/btn">
                <span>Read Story</span>
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-3.5 h-3.5 group-hover/btn:translate-x-0.5 transition-transform">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
                </svg>
              </button>
            </div>
          </div>

        </div>
      </div>

      <div class="flex flex-col md:flex-row items-stretch md:items-center justify-between gap-4 pt-4">
        
        <div class="flex items-center gap-2 overflow-x-auto pb-2 md:pb-0 scrollbar-none">
          <button 
            v-for="cat in categories" 
            :key="cat"
            @click="selectedCategory = cat"
            class="px-4 py-2 rounded-xl text-xs font-heading font-bold whitespace-nowrap transition-all duration-200 shrink-0"
            :class="selectedCategory === cat 
              ? 'bg-zinc-900 text-white shadow-md' 
              : 'bg-white text-zinc-600 hover:bg-stone-200/70 border border-zinc-200/80'"
          >
            {{ cat }}
          </button>
        </div>

        <div class="relative w-full md:w-72 flex items-center px-3.5 py-2.5 bg-white rounded-xl border border-zinc-200/80 shadow-sm focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4 text-zinc-400 shrink-0 mr-2.5">
            <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
          </svg>
          <input 
            v-model="searchQuery"
            type="text" 
            placeholder="Search stories..." 
            class="w-full bg-transparent text-xs font-sans font-semibold text-zinc-900 placeholder-zinc-400 focus:outline-none"
          />
        </div>

      </div>

      <div v-if="filteredPosts.length > 0" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <article 
          v-for="post in filteredPosts" 
          :key="post.id" 
          class="bg-white rounded-3xl border border-zinc-200/80 shadow-md hover:shadow-xl transition-all duration-300 flex flex-col justify-between overflow-hidden group"
        >
          <div>
            <div class="relative h-52 overflow-hidden bg-zinc-900">
              <img 
                :src="post.image" 
                :alt="post.title" 
                class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500 opacity-95"
              />
              <div class="absolute top-3 left-3 bg-white/90 backdrop-blur-md px-2.5 py-1 rounded-lg text-zinc-900 text-[11px] font-heading font-bold shadow-sm">
                {{ post.category }}
              </div>
            </div>

            <div class="p-6 space-y-3">
              <div class="flex items-center gap-2 text-xs font-sans font-medium text-zinc-400">
                <span>{{ post.date }}</span>
                <span>•</span>
                <span>{{ post.readTime }}</span>
              </div>

              <h3 class="font-heading text-lg font-bold text-zinc-900 leading-snug group-hover:text-emerald-600 transition-colors cursor-pointer">
                {{ post.title }}
              </h3>

              <p class="font-sans text-xs text-zinc-600 font-medium leading-relaxed line-clamp-3">
                {{ post.excerpt }}
              </p>
            </div>
          </div>

          <div class="px-6 pb-6 pt-2 border-t border-zinc-100/80 flex items-center justify-between">
            <div class="flex items-center gap-2.5">
              <img :src="post.author.avatar" :alt="post.author.name" class="w-8 h-8 rounded-lg object-cover" />
              <div>
                <p class="font-heading text-xs font-bold text-zinc-900 leading-tight">{{ post.author.name }}</p>
                <p class="font-sans text-[10px] text-zinc-400 font-medium">{{ post.author.role }}</p>
              </div>
            </div>

            <button class="w-8 h-8 rounded-xl bg-stone-100 group-hover:bg-emerald-600 group-hover:text-white text-zinc-700 flex items-center justify-center transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4">
                <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
              </svg>
            </button>
          </div>
        </article>
      </div>

      <div v-else class="bg-white p-12 rounded-3xl border border-zinc-200/80 text-center space-y-3">
        <div class="w-12 h-12 rounded-2xl bg-stone-100 text-zinc-400 flex items-center justify-center mx-auto">
          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
            <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
          </svg>
        </div>
        <h3 class="font-heading text-lg font-bold text-zinc-900">No stories found</h3>
        <p class="font-sans text-xs text-zinc-500 font-medium max-w-sm mx-auto">
          We couldn't find any articles matching your query. Try resetting your category filter or search term.
        </p>
        <button 
          @click="selectedCategory = 'All'; searchQuery = ''" 
          class="px-4 py-2 bg-stone-100 hover:bg-stone-200 text-zinc-800 font-sans font-bold text-xs rounded-xl transition-all"
        >
          Reset Filters
        </button>
      </div>

      <div class="bg-zinc-900 text-white p-8 sm:p-12 rounded-3xl shadow-xl border border-zinc-800 relative overflow-hidden">
        <div class="absolute top-0 right-0 -mt-8 -mr-8 w-64 h-64 bg-emerald-500/10 rounded-full blur-2xl pointer-events-none"></div>
        
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center relative z-10">
          <div class="lg:col-span-7 space-y-2">
            <p class="font-heading text-xs font-bold text-amber-400 uppercase tracking-wider">Stay Connected</p>
            <h3 class="font-heading text-2xl sm:text-3xl font-black text-white">Get secret travel guides delivered weekly</h3>
            <p class="font-sans text-xs sm:text-sm text-stone-300 font-medium leading-relaxed">
              No spam. Just handpicked stories, neighborhood guides, and exclusive local tour recommendations.
            </p>
          </div>

          <div class="lg:col-span-5">
            <form @submit.prevent="handleSubscribe" class="flex flex-col sm:flex-row items-center gap-3">
              <input 
                v-model="newsletterEmail"
                type="email" 
                placeholder="Enter your email address" 
                class="w-full px-4 py-3 bg-zinc-800 border border-zinc-700/80 rounded-xl text-xs font-sans text-white placeholder-zinc-500 focus:outline-none focus:border-emerald-500 transition-all"
                required
              />
              <button 
                type="submit" 
                class="w-full sm:w-auto px-6 py-3 bg-emerald-600 hover:bg-emerald-500 text-white font-sans font-bold text-xs rounded-xl shadow-md transition-all shrink-0"
              >
                Subscribe
              </button>
            </form>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>