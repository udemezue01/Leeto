<script setup>
import { ref } from 'vue'

const openIndex = ref(0) // Default first item open

const faqs = ref([
  {
    question: 'How does booking a local guide on Leeto work?',
    answer: 'Search your destination, browse verified local guide profiles, choose an experience, and select your preferred date and time. Once you submit a booking request, your host confirms within 24 hours.'
  },
  {
    question: 'Are tours private or will I join other travelers?',
    answer: 'All experiences on Leeto are 100% private by default. You and your party will have your guide’s undivided attention, allowing for a fully customized pace and itinerary.'
  },
  {
    question: 'What is Leeto’s cancellation policy?',
    answer: 'We offer full refunds for cancellations made up to 48 hours before your scheduled tour start time. Cancellations made within 48 hours can be rescheduled based on host availability.'
  },
  {
    question: 'How are local guides vetted and verified?',
    answer: 'Every guide undergoes a multi-step verification process, including identity checks, background screenings, live video interviews, and review monitoring to ensure safety and exceptional quality.'
  },
  {
    question: 'Can I request a custom itinerary?',
    answer: 'Yes! After booking (or via the "Contact Host" button on their profile), you can message your guide directly to tailor food preferences, mobility needs, or specific sights you want to visit.'
  },
  {
    question: 'What is included in the tour price?',
    answer: 'Each tour listing explicitly details what is included—such as tastings, entrance tickets, or transport. Your guide’s time and personalized expertise are always covered.'
  }
])

const toggleFaq = (index) => {
  openIndex.value = openIndex.value === index ? null : index
}
</script>

<template>
  <section class="bg-stone-50 py-16 sm:py-24 text-zinc-800 font-sans border-t border-zinc-200/80">
    <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- Section Header -->
      <div class="text-center mb-12 sm:mb-16">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-emerald-100/80 border border-emerald-200/60 text-emerald-800 text-xs font-bold uppercase tracking-wider mb-3">
          <span>❓</span> Good to Know
        </div>
        <h2 class="text-3xl sm:text-4xl font-black text-zinc-900 tracking-tight">
          Frequently Asked Questions
        </h2>
        <p class="mt-3 text-sm sm:text-base text-zinc-600 max-w-xl mx-auto">
          Everything you need to know about booking private tours, custom itineraries, and hosting with Leeto.
        </p>
      </div>

      <!-- FAQ Accordion List -->
      <div class="space-y-4">
        <div 
          v-for="(faq, index) in faqs" 
          :key="index"
          class="bg-white border border-zinc-200/80 rounded-2xl overflow-hidden shadow-sm transition-all duration-200 hover:border-emerald-500/50"
        >
          <button 
            @click="toggleFaq(index)"
            type="button"
            class="w-full text-left px-6 py-5 flex items-center justify-between gap-4 focus:outline-none cursor-pointer select-none"
            :aria-expanded="openIndex === index"
          >
            <span class="text-base sm:text-lg font-bold text-zinc-900">
              {{ faq.question }}
            </span>
            
            <span 
              class="shrink-0 w-8 h-8 rounded-full bg-stone-100 flex items-center justify-center text-zinc-600 transition-transform duration-300"
              :class="{ 'rotate-180 bg-emerald-100 text-emerald-800': openIndex === index }"
            >
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4">
                <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 8.25l-7.5 7.5-7.5-7.5" />
              </svg>
            </span>
          </button>

          <!-- Accordion Body -->
          <div 
            v-show="openIndex === index" 
            class="px-6 pb-5 text-sm sm:text-base text-zinc-600 leading-relaxed border-t border-zinc-100/80 pt-3"
          >
            {{ faq.answer }}
          </div>
        </div>
      </div>

      <!-- Footer Help Link -->
      <div class="mt-12 text-center">
        <p class="text-xs sm:text-sm text-zinc-500">
          Still have questions? 
          <a href="#support" class="font-bold text-emerald-600 hover:text-emerald-700 underline underline-offset-2">
            Contact our 24/7 support team
          </a>
        </p>
      </div>

    </div>
  </section>
</template>