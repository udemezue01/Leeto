<script setup>
import { ref } from 'vue'

const activeSection = ref('introduction')

const scrollToSection = (id) => {
  activeSection.value = id
  const element = document.getElementById(id)
  if (element) {
    // Scroll to the element with a slight offset for the sticky header if you have one
    const y = element.getBoundingClientRect().top + window.scrollY - 40
    window.scrollTo({ top: y, behavior: 'smooth' })
  }
}

const tableOfContents = [
  { id: 'introduction', title: '1. What are Cookies?' },
  { id: 'how-we-use', title: '2. How We Use Cookies' },
  { id: 'types-of-cookies', title: '3. Types of Cookies We Use' },
  { id: 'third-party', title: '4. Third-Party Cookies' },
  { id: 'manage-preferences', title: '5. Managing Your Preferences' },
  { id: 'updates', title: '6. Policy Updates & Contact' }
]
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-20 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen">
    
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 right-0 -mt-12 -mr-12 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 left-0 -mb-12 -ml-12 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute top-1/2 left-1/4 w-[500px] h-[500px] bg-emerald-500/5 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">

      <!-- =============================================================== -->
      <!-- SECTION HEADER                                                  -->
      <!-- =============================================================== -->
      <div class="flex flex-col md:flex-row md:items-end justify-between mb-8 gap-4 border-b border-zinc-200/80 pb-6">
        <div>
          <!-- Badge Indicator -->
          <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider mb-3">
            <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
            Legal & Privacy
          </div>
          <h1 class="text-3xl sm:text-4xl font-black text-zinc-900 tracking-tight">
            Leeto <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">Cookie Policy</span>
          </h1>
          <p class="text-zinc-600 mt-1.5 text-sm sm:text-base font-medium">Transparency on how we collect and use data to improve your travel experience.</p>
        </div>

        <!-- Quick Metrics Summary (Last Updated) -->
        <div class="flex items-center gap-4 text-xs font-semibold text-zinc-600 bg-white px-4 py-3 rounded-2xl border border-zinc-200/80 shadow-sm shrink-0">
          <div class="flex items-center gap-2">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4 text-emerald-600">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 012.25-2.25h13.5A2.25 2.25 0 0121 7.5v11.25m-18 0A2.25 2.25 0 005.25 21h13.5A2.25 2.25 0 0021 18.75m-18 0v-7.5A2.25 2.25 0 015.25 9h13.5A2.25 2.25 0 0121 11.25v7.5" />
            </svg>
            <span>Last Updated: August 21, 2026</span>
          </div>
        </div>
      </div>

      <!-- =============================================================== -->
      <!-- MAIN PAGE LAYOUT: SPLIT INTO 3 PARTS                           -->
      <!-- Part 1: Table of Contents (1 Col) | Parts 2 & 3: Content       -->
      <!-- =============================================================== -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 items-start">

        <!-- ============================================================= -->
        <!-- PART 1: TABLE OF CONTENTS (1 / 3 Columns on Desktop)          -->
        <!-- Sticky on desktop for seamless browsing                        -->
        <!-- ============================================================= -->
        <aside class="lg:col-span-1 hidden lg:block sticky top-8">
          <div class="bg-white rounded-3xl border border-zinc-200/80 shadow-xl shadow-zinc-200/50 p-6 space-y-6">
            
            <div class="flex items-center gap-2.5 border-b border-zinc-100 pb-4">
              <div class="w-8 h-8 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center font-bold">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 6.75h12M8.25 12h12m-12 5.25h12M3.75 6.75h.007v.008H3.75V6.75zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zM3.75 12h.007v.008H3.75V12zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm-.375 5.25h.007v.008H3.75v-.008zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0z" />
                </svg>
              </div>
              <h3 class="font-bold text-zinc-900 text-base">In this policy</h3>
            </div>

            <nav class="space-y-1">
              <button 
                v-for="item in tableOfContents" 
                :key="item.id"
                @click="scrollToSection(item.id)"
                :class="[
                  'w-full text-left px-4 py-2.5 rounded-xl text-sm font-bold transition-all duration-200',
                  activeSection === item.id 
                    ? 'bg-emerald-50 text-emerald-700' 
                    : 'text-zinc-500 hover:bg-stone-100 hover:text-zinc-900'
                ]"
              >
                {{ item.title }}
              </button>
            </nav>

            <div class="pt-4 border-t border-zinc-100">
              <button class="w-full py-3 px-4 bg-zinc-900 hover:bg-emerald-600 text-white text-xs font-bold rounded-xl flex items-center justify-center gap-2 transition duration-200 shadow-md">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 6a7.5 7.5 0 107.5 7.5h-7.5V6z" />
                  <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 10.5H21A7.5 7.5 0 0013.5 3v7.5z" />
                </svg>
                <span>Manage Preferences</span>
              </button>
            </div>
          </div>
        </aside>

        <!-- ============================================================= -->
        <!-- PART 2 & 3: MAIN CONTENT (2 / 3 Columns on Desktop)           -->
        <!-- ============================================================= -->
        <main class="lg:col-span-2 space-y-8">
          
          <div class="bg-white rounded-3xl border border-zinc-200/80 shadow-md p-6 sm:p-10 text-zinc-600 font-medium text-sm sm:text-base leading-relaxed space-y-12">

            <!-- Section 1 -->
            <section id="introduction" class="scroll-mt-8 space-y-4">
              <h2 class="text-2xl font-black text-zinc-900 tracking-tight flex items-center gap-3">
                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-emerald-100 text-emerald-700 text-sm">1</span>
                What are Cookies?
              </h2>
              <p>
                Cookies are small text files that are stored on your browser or device by websites, apps, online media, and advertisements. 
                At <strong>Leeto</strong>, we use cookies and similar technologies to remember your preferences (like your preferred currency or destination searches), keep you logged in safely, and understand how you use our platform to connect with local guides.
              </p>
              <p>
                This policy explains the types of cookies we use, why we use them, and the choices you have to manage them while exploring the world with us.
              </p>
            </section>

            <hr class="border-zinc-200/70" />

            <!-- Section 2 -->
            <section id="how-we-use" class="scroll-mt-8 space-y-4">
              <h2 class="text-2xl font-black text-zinc-900 tracking-tight flex items-center gap-3">
                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-emerald-100 text-emerald-700 text-sm">2</span>
                How We Use Cookies
              </h2>
              <p>We rely on cookies to make your travel planning seamless. Specifically, we use them to:</p>
              <ul class="space-y-3 mt-4">
                <li class="flex items-start gap-3">
                  <svg class="w-5 h-5 text-emerald-500 shrink-0 mt-0.5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5"><path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7"/></svg>
                  <span><strong>Authenticate you:</strong> Keeping you logged in securely whether you are a traveler booking a tour or a local guide managing your availability.</span>
                </li>
                <li class="flex items-start gap-3">
                  <svg class="w-5 h-5 text-emerald-500 shrink-0 mt-0.5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5"><path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7"/></svg>
                  <span><strong>Remember preferences:</strong> Saving your recent destination searches (e.g., Tokyo, Rome), language, and currency choices.</span>
                </li>
                <li class="flex items-start gap-3">
                  <svg class="w-5 h-5 text-emerald-500 shrink-0 mt-0.5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5"><path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7"/></svg>
                  <span><strong>Process payments safely:</strong> Supporting anti-fraud measures when you pay for an experience or when guides receive payouts.</span>
                </li>
              </ul>
            </section>

            <hr class="border-zinc-200/70" />

            <!-- Section 3 -->
            <section id="types-of-cookies" class="scroll-mt-8 space-y-6">
              <h2 class="text-2xl font-black text-zinc-900 tracking-tight flex items-center gap-3">
                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-emerald-100 text-emerald-700 text-sm">3</span>
                Types of Cookies We Use
              </h2>
              
              <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                <div class="bg-stone-50 border border-zinc-200/80 rounded-2xl p-5">
                  <h4 class="text-zinc-900 font-bold mb-2 flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-emerald-500"></span> Essential Cookies
                  </h4>
                  <p class="text-xs text-zinc-500 leading-relaxed">
                    Crucial for the basic functions of Leeto. Without these, you cannot log in, message guides securely, or complete booking transactions. They cannot be disabled.
                  </p>
                </div>
                
                <div class="bg-stone-50 border border-zinc-200/80 rounded-2xl p-5">
                  <h4 class="text-zinc-900 font-bold mb-2 flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-amber-500"></span> Functional Cookies
                  </h4>
                  <p class="text-xs text-zinc-500 leading-relaxed">
                    These allow us to remember choices you make and provide enhanced, more personal features, like remembering your filter settings (e.g., "Private Tours Only").
                  </p>
                </div>

                <div class="bg-stone-50 border border-zinc-200/80 rounded-2xl p-5">
                  <h4 class="text-zinc-900 font-bold mb-2 flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-blue-500"></span> Performance Cookies
                  </h4>
                  <p class="text-xs text-zinc-500 leading-relaxed">
                    Help us understand how travelers interact with our platform by collecting and reporting information anonymously to improve site speed and UX.
                  </p>
                </div>

                <div class="bg-stone-50 border border-zinc-200/80 rounded-2xl p-5">
                  <h4 class="text-zinc-900 font-bold mb-2 flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-purple-500"></span> Targeting Cookies
                  </h4>
                  <p class="text-xs text-zinc-500 leading-relaxed">
                    Set by our advertising partners to build a profile of your interests and show you relevant local experiences on other sites.
                  </p>
                </div>
              </div>
            </section>

            <hr class="border-zinc-200/70" />

            <!-- Section 4 -->
            <section id="third-party" class="scroll-mt-8 space-y-4">
              <h2 class="text-2xl font-black text-zinc-900 tracking-tight flex items-center gap-3">
                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-emerald-100 text-emerald-700 text-sm">4</span>
                Third-Party Cookies
              </h2>
              <p>
                In some special cases, we also use cookies provided by trusted third parties. For example:
              </p>
              <ul class="list-disc list-inside space-y-2 ml-2 text-zinc-600">
                <li><strong>Analytics:</strong> We use Google Analytics to help us understand how you use the site and ways that we can improve your experience.</li>
                <li><strong>Payment Gateways:</strong> Providers like Stripe or PayPal may place cookies to verify identity and process tour bookings safely.</li>
                <li><strong>Social Media:</strong> Buttons and plugins that allow you to connect with your social network may set cookies through our site.</li>
              </ul>
            </section>

            <hr class="border-zinc-200/70" />

            <!-- Section 5 -->
            <section id="manage-preferences" class="scroll-mt-8 space-y-4">
              <h2 class="text-2xl font-black text-zinc-900 tracking-tight flex items-center gap-3">
                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-emerald-100 text-emerald-700 text-sm">5</span>
                Managing Your Preferences
              </h2>
              <p>
                You can adjust your cookie preferences at any time. While essential cookies cannot be disabled, you can opt-out of functional, performance, and targeting cookies.
              </p>
              <div class="mt-6 p-6 bg-emerald-50/50 border border-emerald-100 rounded-2xl flex flex-col sm:flex-row items-center justify-between gap-4">
                <div>
                  <h4 class="font-bold text-zinc-900">Cookie Preference Center</h4>
                  <p class="text-xs text-zinc-500 mt-1">Review and update your current cookie consents.</p>
                </div>
                <button class="w-full sm:w-auto px-6 py-2.5 bg-zinc-900 hover:bg-emerald-600 text-white text-sm font-bold rounded-xl transition duration-200 shrink-0 shadow-md">
                  Update Settings
                </button>
              </div>
              <p class="text-sm mt-4">
                Alternatively, most web browsers allow some control of most cookies through the browser settings. To find out more about cookies, including how to see what cookies have been set, visit <a href="#" class="text-emerald-600 font-bold hover:underline">aboutcookies.org</a>.
              </p>
            </section>

            <hr class="border-zinc-200/70" />

            <!-- Section 6 -->
            <section id="updates" class="scroll-mt-8 space-y-4">
              <h2 class="text-2xl font-black text-zinc-900 tracking-tight flex items-center gap-3">
                <span class="flex items-center justify-center w-8 h-8 rounded-lg bg-emerald-100 text-emerald-700 text-sm">6</span>
                Updates & Contact
              </h2>
              <p>
                We may update this Cookie Policy from time to time in order to reflect changes to the cookies we use or for other operational, legal, or regulatory reasons. Please revisit this Cookie Policy regularly to stay informed.
              </p>
              <div class="mt-6 p-6 bg-zinc-900 text-white rounded-2xl">
                <h4 class="font-bold text-white mb-2">Have questions?</h4>
                <p class="text-sm text-stone-300 mb-4">
                  If you have any questions about our use of cookies or other technologies, please contact our privacy team.
                </p>
                <a href="mailto:privacy@leeto.com" class="inline-flex items-center gap-2 px-4 py-2 bg-stone-800 hover:bg-emerald-600 border border-zinc-700 rounded-xl text-sm font-bold transition-colors duration-200">
                  <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-4 h-4">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" />
                  </svg>
                  privacy@leeto.com
                </a>
              </div>
            </section>

          </div>
        </main>
      </div>

    </div>
  </section>
</template>