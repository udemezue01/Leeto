<script setup>
import { ref, computed } from 'vue'

const searchQuery = ref('')
const activeTab = ref('all') // 'all' | 'travelers' | 'guides'
const openFaq = ref(null)

const toggleFaq = (index) => {
  openFaq.value = openFaq.value === index ? null : index
}

const categories = [
  {
    id: 'booking',
    title: 'Booking & Payments',
    description: 'Payment methods, receipts, currencies, and instant confirmation.',
    icon: 'M2.25 8.25h19.5M2.25 9h19.5pt11.25M2.25 12h19.5M3.75 6h16.5a1.5 1.5 0 011.5 1.5v9a1.5 1.5 0 01-1.5 1.5H3.75a1.5 1.5 0 01-1.5-1.5v-9a1.5 1.5 0 011.5-1.5z'
  },
  {
    id: 'safety',
    title: 'Safety & Verification',
    description: 'Background checks, guide verification standards, and emergency protocols.',
    icon: 'M9 12.75L11.25 15 15 9.75m-3-7.036A11.959 11.959 0 013.598 6 11.99 11.99 0 003 9.749c0 5.592 3.824 10.29 9 11.623 5.176-1.332 9-6.03 9-11.622 0-1.31-.21-2.571-.598-3.751A11.959 11.959 0 0112 2.714z'
  },
  {
    id: 'cancellation',
    title: 'Cancellations & Refunds',
    description: 'Understanding our 24-hour free cancellation policy and refund timelines.',
    icon: 'M16.023 9.348h4.992v-.001M2.985 19.644v-4.992m0 0h4.992m-4.993 0l3.181 3.183a8.25 8.25 0 0013.803-3.7M4.031 9.865a8.25 8.25 0 0113.803-3.7l3.181 3.182m0-4.991v4.99'
  },
  {
    id: 'guides',
    title: 'Hosting & Payouts',
    description: 'Setting tour rates, earning payouts, and managing direct bookings.',
    icon: 'M12 6v12m-3-6h6m-7 6h8a2 2 0 002-2V8a2 2 0 00-2-2H7a2 2 0 00-2 2v8a2 2 0 002 2z'
  }
]

const faqs = [
  {
    target: 'travelers',
    question: 'How do I customize a private tour with a local guide?',
    answer: 'Once you select a guide, click "Contact Guide" on their profile. You can message them directly to discuss specific interests, request dietary accommodations, or tweak starting times before confirming your booking.'
  },
  {
    target: 'travelers',
    question: 'What is Leeto’s cancellation and refund policy?',
    answer: 'Bookings canceled at least 24 hours prior to the scheduled tour start time receive a 100% full refund. Cancellations made within 24 hours are subject to host approval depending on prepared itinerary arrangements.'
  },
  {
    target: 'travelers',
    question: 'How are local guides verified on Leeto?',
    answer: 'Every guide on Leeto undergoes identity verification, local background screening, and an interview process with our quality team. We also continuously monitor traveler reviews to ensure safety and excellence.'
  },
  {
    target: 'guides',
    question: 'How and when do guides get paid?',
    answer: 'Payouts are automatically processed 24 hours after a tour is successfully completed. Earnings are transferred directly to your connected bank account or payout method of choice without extra transfer fees.'
  },
  {
    target: 'guides',
    question: 'Can I set my own prices and schedule?',
    answer: 'Yes! As a Leeto guide, you have 100% control over your hourly or per-person pricing, availability calendar, minimum group size, and maximum guest limit.'
  },
  {
    target: 'guides',
    question: 'What happens if a traveler cancels at the last minute?',
    answer: 'If a traveler cancels within 24 hours of the experience or fails to show up, guides are protected by our cancellation policy and receive their full expected payout.'
  }
]

const filteredFaqs = computed(() => {
  return faqs.filter(faq => {
    const matchesTab = activeTab.value === 'all' || faq.target === activeTab.value
    const matchesQuery = searchQuery.value === '' || 
      faq.question.toLowerCase().includes(searchQuery.value.toLowerCase()) || 
      faq.answer.toLowerCase().includes(searchQuery.value.toLowerCase())
    return matchesTab && matchesQuery
  })
})
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen">
    
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-16">

      <!-- =============================================================== -->
      <!-- HERO SEARCH BANNER                                              -->
      <!-- =============================================================== -->
      <div class="text-center max-w-3xl mx-auto space-y-6">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
          24/7 Global Support Center
        </div>

        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
          How can we <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">help you?</span>
        </h1>

        <!-- Search Bar -->
        <div class="bg-white p-3 sm:p-4 rounded-2xl sm:rounded-3xl shadow-xl shadow-zinc-200/60 border border-zinc-200/80 max-w-2xl mx-auto">
          <div class="relative flex items-center px-3 py-2.5 bg-stone-50 rounded-xl border border-zinc-200/70 focus-within:border-emerald-600 focus-within:ring-1 focus-within:ring-emerald-600 transition-all">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-5 h-5 text-emerald-600 shrink-0 mr-2.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
            </svg>
            <input 
              v-model="searchQuery"
              type="text" 
              placeholder="Search for answers e.g. cancellations, payouts, verification..." 
              class="w-full bg-transparent text-zinc-900 placeholder-zinc-400 text-sm font-semibold focus:outline-none"
            />
          </div>
        </div>
      </div>

      <!-- =============================================================== -->
      <!-- TOP HELP CATEGORIES                                             -->
      <!-- =============================================================== -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <div 
          v-for="category in categories" 
          :key="category.id"
          class="bg-white p-6 rounded-2xl sm:rounded-3xl border border-zinc-200/80 shadow-md hover:shadow-xl hover:-translate-y-1 transition-all duration-200 cursor-pointer group flex flex-col justify-between"
        >
          <div>
            <div class="w-12 h-12 rounded-2xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold mb-5 group-hover:bg-zinc-900 group-hover:text-white transition-colors">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" :d="category.icon" />
              </svg>
            </div>
            <h3 class="text-lg font-bold text-zinc-900 mb-2 group-hover:text-emerald-600 transition-colors">{{ category.title }}</h3>
            <p class="text-xs text-zinc-500 font-medium leading-relaxed">{{ category.description }}</p>
          </div>
          <div class="mt-6 flex items-center gap-1.5 text-xs font-bold text-emerald-600">
            <span>Browse Topics</span>
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-3.5 h-3.5 group-hover:translate-x-1 transition-transform">
              <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
            </svg>
          </div>
        </div>
      </div>

      <!-- =============================================================== -->
      <!-- FREQUENTLY ASKED QUESTIONS SECTION                             -->
      <!-- =============================================================== -->
      <div class="bg-white rounded-3xl border border-zinc-200/80 p-6 sm:p-10 shadow-xl shadow-zinc-200/50 space-y-8">
        
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 border-b border-zinc-100 pb-6">
          <div>
            <h2 class="text-2xl sm:text-3xl font-black text-zinc-900 tracking-tight">Frequently Asked Questions</h2>
            <p class="text-xs sm:text-sm text-zinc-500 font-medium mt-1">Quick answers to common questions from our community.</p>
          </div>

          <!-- FAQ Filter Tabs -->
          <div class="inline-flex p-1 bg-stone-100 rounded-xl border border-zinc-200/70 self-start sm:self-auto">
            <button 
              @click="activeTab = 'all'"
              :class="['px-3.5 py-1.5 rounded-lg text-xs font-bold transition-all', activeTab === 'all' ? 'bg-white text-zinc-900 shadow-sm' : 'text-zinc-500 hover:text-zinc-900']"
            >
              All
            </button>
            <button 
              @click="activeTab = 'travelers'"
              :class="['px-3.5 py-1.5 rounded-lg text-xs font-bold transition-all', activeTab === 'travelers' ? 'bg-white text-zinc-900 shadow-sm' : 'text-zinc-500 hover:text-zinc-900']"
            >
              Travelers
            </button>
            <button 
              @click="activeTab = 'guides'"
              :class="['px-3.5 py-1.5 rounded-lg text-xs font-bold transition-all', activeTab === 'guides' ? 'bg-white text-zinc-900 shadow-sm' : 'text-zinc-500 hover:text-zinc-900']"
            >
              Guides
            </button>
          </div>
        </div>

        <!-- FAQ Accordion List -->
        <div class="space-y-4">
          <div 
            v-for="(faq, index) in filteredFaqs" 
            :key="index"
            class="border border-zinc-200/70 rounded-2xl transition-all duration-200 overflow-hidden"
            :class="openFaq === index ? 'bg-stone-50/80 border-emerald-600/50' : 'bg-white hover:border-zinc-300'"
          >
            <button 
              @click="toggleFaq(index)"
              class="w-full px-6 py-4 text-left flex items-center justify-between gap-4 focus:outline-none"
            >
              <span class="text-sm sm:text-base font-bold text-zinc-900 flex items-center gap-3">
                <span class="w-2 h-2 rounded-full shrink-0" :class="faq.target === 'travelers' ? 'bg-emerald-500' : 'bg-amber-500'"></span>
                {{ faq.question }}
              </span>
              <svg 
                xmlns="http://www.w3.org/2000/svg" 
                fill="none" 
                viewBox="0 0 24 24" 
                stroke-width="2.5" 
                stroke="currentColor" 
                class="w-4 h-4 text-zinc-500 shrink-0 transition-transform duration-200"
                :class="openFaq === index ? 'rotate-180 text-emerald-600' : ''"
              >
                <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
              </svg>
            </button>
            <div 
              v-show="openFaq === index" 
              class="px-6 pb-5 pt-1 text-xs sm:text-sm text-zinc-600 font-medium leading-relaxed border-t border-zinc-100"
            >
              {{ faq.answer }}
            </div>
          </div>

          <div v-if="filteredFaqs.length === 0" class="text-center py-10 text-zinc-500 font-medium text-sm">
            No FAQs matching your search query. Try typing another term or contact support below.
          </div>
        </div>

      </div>

      <!-- =============================================================== -->
      <!-- STILL NEED HELP / CONTACT CTA                                   -->
      <!-- =============================================================== -->
      <div class="bg-zinc-900 rounded-3xl p-6 sm:p-10 lg:p-12 text-white relative overflow-hidden shadow-2xl border border-zinc-800">
        <div class="absolute top-0 right-0 -mt-10 -mr-10 w-80 h-80 bg-emerald-500/20 rounded-full blur-3xl pointer-events-none"></div>

        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center relative z-10">
          <div class="lg:col-span-8 space-y-4 text-center lg:text-left">
            <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-400 text-xs font-bold uppercase tracking-wider border border-emerald-500/30">
              💬 Direct Assistance
            </div>
            <h2 class="text-3xl sm:text-4xl font-black text-white tracking-tight">
              Still have questions? We're here for you.
            </h2>
            <p class="text-stone-300 font-medium text-sm sm:text-base max-w-xl">
              Our support team is active around the clock to help with active tour emergencies, booking adjustments, and account verification.
            </p>
          </div>

          <div class="lg:col-span-4 flex flex-col sm:flex-row lg:flex-col gap-3 justify-center">
            <button class="w-full py-3.5 px-6 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-sm rounded-xl shadow-lg transition-all duration-200 flex items-center justify-center gap-2">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                <path stroke-linecap="round" stroke-linejoin="round" d="M8.625 12a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0H8.25m4.125 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0H12m4.125 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm0 0h-.375M21 12c0 4.556-4.03 8.25-9 8.25a9.764 9.764 0 01-2.555-.337A5.972 5.972 0 015.41 20.97a.75.75 0 01-.81-.54 5.96 5.96 0 011.207-3.056C4.41 15.82 3 14.02 3 12c0-4.556 4.03-8.25 9-8.25s9 3.694 9 8.25z" />
              </svg>
              <span>Start Live 24/7 Chat</span>
            </button>
            <button class="w-full py-3.5 px-6 bg-zinc-800 hover:bg-zinc-700 text-white font-bold text-sm rounded-xl border border-zinc-700 transition-all duration-200 flex items-center justify-center gap-2">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                <path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" />
              </svg>
              <span>Email Support</span>
            </button>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>