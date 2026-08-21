<script setup>
import { ref } from 'vue'

const activeSection = ref('collection')

const sections = [
  { id: 'collection', label: '1. Information We Collect' },
  { id: 'usage', label: '2. How We Use Your Data' },
  { id: 'sharing', label: '3. Data Sharing & Safety' },
  { id: 'rights', label: '4. Your Rights & Choices' },
  { id: 'cookies', label: '5. Cookies & Location' },
  { id: 'contact', label: '6. Privacy Contact' }
]

const scrollToSection = (id) => {
  activeSection.value = id
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen">
    
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 space-y-12">

      <!-- =============================================================== -->
      <!-- SECTION HEADER                                                  -->
      <!-- =============================================================== -->
      <div class="text-center max-w-3xl mx-auto space-y-4">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
          Trust, Safety & Transparency
        </div>

        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
          Your privacy is safe <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">with Leeto.</span>
        </h1>

        <p class="text-base sm:text-lg text-zinc-600 font-medium leading-relaxed">
          We believe authentic global travel requires absolute trust. Here is a transparent breakdown of how we collect, protect, and handle your personal data.
        </p>

        <p class="text-xs font-bold text-zinc-400 uppercase tracking-widest pt-2">
          Last Updated: August 2026
        </p>
      </div>

      <!-- =============================================================== -->
      <!-- PRIVACY HIGHLIGHTS SUMMARY GRID                                 -->
      <!-- =============================================================== -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div class="bg-white p-6 rounded-3xl border border-zinc-200/80 shadow-md shadow-zinc-200/40 space-y-3">
          <div class="w-10 h-10 rounded-2xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold text-lg">
            🛡️
          </div>
          <h3 class="font-bold text-zinc-900 text-base">We Never Sell Your Data</h3>
          <p class="text-xs text-zinc-600 font-medium leading-relaxed">
            Your personal contact details, trip preferences, and chat logs are never rented or sold to third-party advertisers.
          </p>
        </div>

        <div class="bg-white p-6 rounded-3xl border border-zinc-200/80 shadow-md shadow-zinc-200/40 space-y-3">
          <div class="w-10 h-10 rounded-2xl bg-amber-100 text-amber-800 flex items-center justify-center font-bold text-lg">
            🔒
          </div>
          <h3 class="font-bold text-zinc-900 text-base">Bank-Grade Encryption</h3>
          <p class="text-xs text-zinc-600 font-medium leading-relaxed">
            All payment processing and guide identity verification documents are transmitted using TLS 1.3 encryption.
          </p>
        </div>

        <div class="bg-white p-6 rounded-3xl border border-zinc-200/80 shadow-md shadow-zinc-200/40 space-y-3">
          <div class="w-10 h-10 rounded-2xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold text-lg">
            📍
          </div>
          <h3 class="font-bold text-zinc-900 text-base">You Control Location</h3>
          <p class="text-xs text-zinc-600 font-medium leading-relaxed">
            Location sharing is strictly opt-in and only active during booked tour windows to help local guides locate you.
          </p>
        </div>
      </div>

      <!-- =============================================================== -->
      <!-- MAIN PAGE LAYOUT: STICKY TOC SIDEBAR + CONTENT AREA             -->
      <!-- =============================================================== -->
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 pt-4">

        <!-- Left Navigation Sidebar (4 cols) -->
        <aside class="lg:col-span-4">
          <div class="bg-white rounded-3xl border border-zinc-200/80 shadow-xl shadow-zinc-200/50 p-6 lg:sticky lg:top-8 space-y-6">
            <h3 class="text-xs font-bold text-zinc-400 uppercase tracking-widest border-b border-zinc-100 pb-3">
              Table of Contents
            </h3>

            <nav class="space-y-1.5">
              <button
                v-for="item in sections"
                :key="item.id"
                @click="scrollToSection(item.id)"
                :class="[
                  'w-full text-left px-4 py-3 rounded-2xl text-xs sm:text-sm font-bold transition-all duration-200 flex items-center justify-between',
                  activeSection === item.id 
                    ? 'bg-zinc-900 text-white shadow-md' 
                    : 'text-zinc-600 hover:bg-stone-100 hover:text-zinc-900'
                ]"
              >
                <span>{{ item.label }}</span>
                <span v-if="activeSection === item.id" class="w-2 h-2 rounded-full bg-emerald-400"></span>
              </button>
            </nav>

            <!-- Quick Support Card -->
            <div class="p-4 bg-stone-50 rounded-2xl border border-zinc-200/70 space-y-2">
              <p class="text-xs font-bold text-zinc-900">Have a privacy question?</p>
              <p class="text-[11px] text-zinc-500 font-medium leading-relaxed">
                Contact our Data Protection Officer directly for assistance.
              </p>
              <a href="mailto:privacy@leeto.com" class="inline-block text-xs font-bold text-emerald-600 hover:underline pt-1">
                privacy@leeto.com →
              </a>
            </div>
          </div>
        </aside>

        <!-- Right Content Area (8 cols) -->
        <main class="lg:col-span-8 space-y-8">
          <div class="bg-white rounded-3xl border border-zinc-200/80 shadow-xl shadow-zinc-200/50 p-6 sm:p-10 space-y-10">

            <!-- Section 1 -->
            <section id="collection" class="space-y-4 scroll-mt-10">
              <div class="flex items-center gap-3">
                <span class="w-8 h-8 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold text-xs">01</span>
                <h2 class="text-xl sm:text-2xl font-black text-zinc-900">Information We Collect</h2>
              </div>
              <p class="text-sm text-zinc-600 font-medium leading-relaxed">
                To facilitate authentic tour bookings between travelers and local guides, we collect specific information based on how you interact with the platform.
              </p>

              <blockquote class="p-4 bg-stone-50 border-l-4 border-emerald-500 rounded-r-2xl text-xs sm:text-sm text-zinc-700 font-medium leading-relaxed">
                <strong>Key Principle:</strong> We only request data that is strictly necessary to ensure user safety, identity verification, and tour fulfillment.
              </blockquote>

              <div class="space-y-3 pt-2">
                <h4 class="text-xs font-bold uppercase tracking-wider text-zinc-900">A. For Travelers</h4>
                <ul class="list-disc pl-5 text-xs sm:text-sm text-zinc-600 font-medium space-y-1.5">
                  <li><strong>Account Setup:</strong> Full name, email address, phone number, and profile photo.</li>
                  <li><strong>Booking Details:</strong> Destination preferences, travel dates, dietary restrictions, and custom tour requests.</li>
                  <li><strong>Payment Info:</strong> Tokenized credit card or wallet details processed securely via Stripe or PayPal.</li>
                </ul>
              </div>

              <div class="space-y-3 pt-2">
                <h4 class="text-xs font-bold uppercase tracking-wider text-zinc-900">B. For Local Guides</h4>
                <ul class="list-disc pl-5 text-xs sm:text-sm text-zinc-600 font-medium space-y-1.5">
                  <li><strong>Identity Verification:</strong> Government-issued ID, background check credentials, and proof of residence.</li>
                  <li><strong>Payout Details:</strong> Bank account routing numbers or supported payout provider credentials.</li>
                  <li><strong>Listing Content:</strong> Experience titles, bio, language fluencies, and guide availability calendar.</li>
                </ul>
              </div>
            </section>

            <hr class="border-zinc-100" />

            <!-- Section 2 -->
            <section id="usage" class="space-y-4 scroll-mt-10">
              <div class="flex items-center gap-3">
                <span class="w-8 h-8 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold text-xs">02</span>
                <h2 class="text-xl sm:text-2xl font-black text-zinc-900">How We Use Your Data</h2>
              </div>
              <p class="text-sm text-zinc-600 font-medium leading-relaxed">
                Your data powers the core Leeto experience. We process your information for the following operational purposes:
              </p>

              <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 pt-2">
                <div class="p-4 bg-stone-50 rounded-2xl border border-zinc-200/60">
                  <h4 class="text-xs font-bold text-zinc-900 mb-1">Tour Connection</h4>
                  <p class="text-xs text-zinc-500 font-medium leading-relaxed">Enabling direct messaging and itinerary customization between confirmed travelers and hosts.</p>
                </div>
                <div class="p-4 bg-stone-50 rounded-2xl border border-zinc-200/60">
                  <h4 class="text-xs font-bold text-zinc-900 mb-1">Payment Escrow</h4>
                  <p class="text-xs text-zinc-500 font-medium leading-relaxed">Holding traveler funds securely in escrow until 24 hours after tour completion.</p>
                </div>
                <div class="p-4 bg-stone-50 rounded-2xl border border-zinc-200/60">
                  <h4 class="text-xs font-bold text-zinc-900 mb-1">Safety & Screening</h4>
                  <p class="text-xs text-zinc-500 font-medium leading-relaxed">Conducting mandatory background checks on guides to maintain community trust.</p>
                </div>
                <div class="p-4 bg-stone-50 rounded-2xl border border-zinc-200/60">
                  <h4 class="text-xs font-bold text-zinc-900 mb-1">Platform Optimization</h4>
                  <p class="text-xs text-zinc-500 font-medium leading-relaxed">Improving search algorithms, category filters, and mobile user responsiveness.</p>
                </div>
              </div>
            </section>

            <hr class="border-zinc-100" />

            <!-- Section 3 -->
            <section id="sharing" class="space-y-4 scroll-mt-10">
              <div class="flex items-center gap-3">
                <span class="w-8 h-8 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold text-xs">03</span>
                <h2 class="text-xl sm:text-2xl font-black text-zinc-900">Data Sharing & Safety</h2>
              </div>
              <p class="text-sm text-zinc-600 font-medium leading-relaxed">
                We strictly limit who sees your personal information. Information is shared only under the following explicit conditions:
              </p>

              <ul class="list-disc pl-5 text-xs sm:text-sm text-zinc-600 font-medium space-y-2">
                <li><strong>Between Travelers & Guides:</strong> Once a tour booking is confirmed, relevant first names and phone numbers are shared to coordinate meeting points.</li>
                <li><strong>Verified Service Providers:</strong> Trusted third parties handling identity verification, cloud hosting, and secure payment processing under strict confidentiality contracts.</li>
                <li><strong>Legal Requirements:</strong> Disclosures made only if required by valid law enforcement requests or court orders.</li>
              </ul>
            </section>

            <hr class="border-zinc-100" />

            <!-- Section 4 -->
            <section id="rights" class="space-y-4 scroll-mt-10">
              <div class="flex items-center gap-3">
                <span class="w-8 h-8 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold text-xs">04</span>
                <h2 class="text-xl sm:text-2xl font-black text-zinc-900">Your Rights & Control</h2>
              </div>
              <p class="text-sm text-zinc-600 font-medium leading-relaxed">
                Regardless of your location, Leeto grants all registered users comprehensive data privacy rights compliant with GDPR and global standards:
              </p>

              <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 pt-2">
                <div class="p-3.5 bg-stone-50 rounded-xl border border-zinc-200/60 text-center">
                  <p class="text-xs font-bold text-zinc-900">Access & Export</p>
                  <p class="text-[11px] text-zinc-500 font-medium mt-1">Download a copy of your personal data file.</p>
                </div>
                <div class="p-3.5 bg-stone-50 rounded-xl border border-zinc-200/60 text-center">
                  <p class="text-xs font-bold text-zinc-900">Correction</p>
                  <p class="text-[11px] text-zinc-500 font-medium mt-1">Update incorrect account or profile information.</p>
                </div>
                <div class="p-3.5 bg-stone-50 rounded-xl border border-zinc-200/60 text-center">
                  <p class="text-xs font-bold text-zinc-900">Right to Erasure</p>
                  <p class="text-[11px] text-zinc-500 font-medium mt-1">Permanently delete your account and records.</p>
                </div>
              </div>
            </section>

            <hr class="border-zinc-100" />

            <!-- Section 5 -->
            <section id="cookies" class="space-y-4 scroll-mt-10">
              <div class="flex items-center gap-3">
                <span class="w-8 h-8 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold text-xs">05</span>
                <h2 class="text-xl sm:text-2xl font-black text-zinc-900">Cookies & Location Services</h2>
              </div>
              <p class="text-sm text-zinc-600 font-medium leading-relaxed">
                Leeto uses essential session cookies to keep you signed in and remember filter selections. You can toggle non-essential analytical cookies anytime via your browser settings.
              </p>
            </section>

            <hr class="border-zinc-100" />

            <!-- Section 6: Dark Contact Banner -->
            <section id="contact" class="bg-zinc-900 rounded-3xl p-6 sm:p-8 text-white space-y-4 relative overflow-hidden shadow-2xl border border-zinc-800 scroll-mt-10">
              <div class="absolute top-0 right-0 -mt-10 -mr-10 w-64 h-64 bg-emerald-500/20 rounded-full blur-3xl pointer-events-none"></div>

              <div class="relative z-10 space-y-2">
                <span class="text-emerald-400 text-xs font-bold uppercase tracking-wider">06. Dedicated Support</span>
                <h3 class="text-2xl font-black text-white">Contact Our Data Protection Officer</h3>
                <p class="text-xs sm:text-sm text-stone-300 font-medium leading-relaxed">
                  If you wish to execute your data rights or have questions regarding our security protocols, please email our legal team.
                </p>
              </div>

              <div class="pt-2 relative z-10 flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 border-t border-zinc-800">
                <div class="text-xs text-stone-400 font-medium">
                  Leeto Global Inc. Attn: Privacy Office
                </div>
                <a href="mailto:privacy@leeto.com" class="px-5 py-2.5 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-xs rounded-xl shadow-md transition-colors">
                  Contact Privacy Team
                </a>
              </div>
            </section>

          </div>
        </main>

      </div>

    </div>
  </section>
</template>