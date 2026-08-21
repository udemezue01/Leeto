<script setup>
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  subject: 'general',
  message: ''
})

const isSubmitting = ref(false)
const showSuccess = ref(false)

const handleSubmit = () => {
  isSubmitting.value = true
  
  // Simulate API call
  setTimeout(() => {
    isSubmitting.value = false
    showSuccess.value = true
    
    // Reset form
    form.value = {
      name: '',
      email: '',
      subject: 'general',
      message: ''
    }
    
    // Hide success message after 5 seconds
    setTimeout(() => {
      showSuccess.value = false
    }, 5000)
  }, 1500)
}
</script>

<template>
  <section class="relative bg-stone-50 py-12 lg:py-24 overflow-hidden font-sans border-b border-zinc-200/60 min-h-screen">
    
    <!-- Ambient Background Glows -->
    <div class="absolute top-0 left-0 -mt-24 -ml-24 w-96 h-96 bg-amber-500/10 rounded-full blur-3xl pointer-events-none"></div>
    <div class="absolute bottom-0 right-0 -mb-24 -mr-24 w-96 h-96 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">

      <!-- =============================================================== -->
      <!-- SECTION HEADER                                                  -->
      <!-- =============================================================== -->
      <div class="text-center max-w-3xl mx-auto mb-16 space-y-6">
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-amber-100/80 border border-amber-200/70 text-amber-900 text-xs font-bold uppercase tracking-wider">
          <span class="flex h-2 w-2 rounded-full bg-amber-500"></span>
          24/7 Global Support
        </div>

        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-black text-zinc-900 tracking-tight leading-[1.12]">
          We’re here to help you <span class="text-emerald-600 underline decoration-amber-400 decoration-wavy decoration-2">explore.</span>
        </h1>

        <p class="text-base sm:text-lg text-zinc-600 font-medium leading-relaxed max-w-2xl mx-auto">
          Whether you have a question about an upcoming trip, need help booking a guide, or want to join us as a local expert, our team is ready.
        </p>
      </div>

      <!-- =============================================================== -->
      <!-- MAIN CONTENT: SPLIT GRID (Contact Info & Form)                  -->
      <!-- =============================================================== -->
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 lg:gap-8 items-start">

        <!-- PART 1: CONTACT INFORMATION (5 Columns) -->
        <div class="lg:col-span-5 space-y-6">
          
          <!-- Email Card -->
          <div class="bg-white p-6 rounded-3xl border border-zinc-200/80 shadow-lg shadow-zinc-200/40 flex items-start gap-4 hover:border-emerald-200 transition-colors group">
            <div class="w-12 h-12 rounded-2xl bg-emerald-100 text-emerald-700 flex items-center justify-center shrink-0 group-hover:scale-105 transition-transform">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" />
              </svg>
            </div>
            <div>
              <h3 class="text-sm font-bold text-zinc-400 uppercase tracking-wider mb-1">Email Us</h3>
              <a href="mailto:support@leeto.com" class="text-lg font-extrabold text-zinc-900 hover:text-emerald-600 transition-colors block">support@leeto.com</a>
              <p class="text-sm text-zinc-500 font-medium mt-1">For general inquiries and booking support.</p>
            </div>
          </div>

          <!-- Partnerships Card -->
          <div class="bg-white p-6 rounded-3xl border border-zinc-200/80 shadow-lg shadow-zinc-200/40 flex items-start gap-4 hover:border-emerald-200 transition-colors group">
            <div class="w-12 h-12 rounded-2xl bg-amber-100 text-amber-700 flex items-center justify-center shrink-0 group-hover:scale-105 transition-transform">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 018.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0111.964-3.07M12 6.375a3.375 3.375 0 11-6.75 0 3.375 3.375 0 016.75 0zm8.25 2.25a2.625 2.625 0 11-5.25 0 2.625 2.625 0 015.25 0z" />
              </svg>
            </div>
            <div>
              <h3 class="text-sm font-bold text-zinc-400 uppercase tracking-wider mb-1">Partnerships & Press</h3>
              <a href="mailto:partners@leeto.com" class="text-lg font-extrabold text-zinc-900 hover:text-emerald-600 transition-colors block">partners@leeto.com</a>
              <p class="text-sm text-zinc-500 font-medium mt-1">For media, collaborations, and B2B inquiries.</p>
            </div>
          </div>

          <!-- FAQ Callout Banner -->
          <div class="bg-zinc-900 p-8 rounded-3xl shadow-xl relative overflow-hidden group">
            <div class="absolute -right-4 -bottom-4 w-32 h-32 bg-emerald-500/20 rounded-full blur-2xl group-hover:bg-emerald-500/30 transition-colors"></div>
            <div class="relative z-10">
              <h3 class="text-xl font-bold text-white mb-2">Need quick answers?</h3>
              <p class="text-sm text-stone-300 font-medium mb-6 line-clamp-2">
                Check out our Help Center for instant answers about payments, cancellations, and guide requirements.
              </p>
              <button class="inline-flex items-center gap-2 px-5 py-2.5 bg-white text-zinc-900 hover:bg-emerald-50 text-sm font-bold rounded-xl transition duration-200">
                Visit Help Center
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
                </svg>
              </button>
            </div>
          </div>

        </div>

        <!-- PART 2: CONTACT FORM (7 Columns) -->
        <div class="lg:col-span-7">
          <div class="bg-white p-6 sm:p-10 rounded-3xl shadow-2xl shadow-zinc-200/60 border border-zinc-200/80 relative overflow-hidden">
            
            <!-- Success Overlay -->
            <div v-if="showSuccess" class="absolute inset-0 bg-white/95 backdrop-blur-sm z-20 flex flex-col items-center justify-center p-8 text-center animate-in fade-in duration-300">
              <div class="w-20 h-20 bg-emerald-100 rounded-full flex items-center justify-center mb-6">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-10 h-10 text-emerald-600">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
                </svg>
              </div>
              <h3 class="text-2xl font-black text-zinc-900 mb-2">Message Sent!</h3>
              <p class="text-zinc-600 font-medium">Thanks for reaching out. A member of our support team will get back to you within 24 hours.</p>
            </div>

            <div class="mb-8">
              <h2 class="text-2xl font-black text-zinc-900">Send us a message</h2>
              <p class="text-sm text-zinc-500 font-medium mt-1">Fill out the form below and we'll be in touch shortly.</p>
            </div>

            <form @submit.prevent="handleSubmit" class="space-y-6">
              
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
                <!-- Name Field -->
                <div>
                  <label class="block text-xs font-bold text-zinc-700 uppercase tracking-wider mb-2">Full Name</label>
                  <input 
                    v-model="form.name"
                    type="text" 
                    required
                    placeholder="e.g. Jane Doe" 
                    class="w-full px-4 py-3 text-sm bg-stone-50 border border-zinc-200/70 rounded-xl focus:outline-none focus:bg-white focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 font-semibold text-zinc-900 placeholder-zinc-400 transition-all"
                  />
                </div>

                <!-- Email Field -->
                <div>
                  <label class="block text-xs font-bold text-zinc-700 uppercase tracking-wider mb-2">Email Address</label>
                  <input 
                    v-model="form.email"
                    type="email" 
                    required
                    placeholder="jane@example.com" 
                    class="w-full px-4 py-3 text-sm bg-stone-50 border border-zinc-200/70 rounded-xl focus:outline-none focus:bg-white focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 font-semibold text-zinc-900 placeholder-zinc-400 transition-all"
                  />
                </div>
              </div>

              <!-- Subject / Category Select -->
              <div>
                <label class="block text-xs font-bold text-zinc-700 uppercase tracking-wider mb-2">How can we help?</label>
                <div class="relative">
                  <select 
                    v-model="form.subject"
                    class="w-full px-4 py-3 text-sm bg-stone-50 border border-zinc-200/70 rounded-xl focus:outline-none focus:bg-white focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 font-semibold text-zinc-900 transition-all cursor-pointer appearance-none"
                  >
                    <option value="general">General Inquiry</option>
                    <option value="booking">Help with a Booking</option>
                    <option value="guide">Becoming a Local Guide</option>
                    <option value="payment">Billing & Payments</option>
                    <option value="feedback">App Feedback / Bug Report</option>
                  </select>
                  <!-- Custom Dropdown Caret -->
                  <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-4 text-zinc-500">
                    <svg class="h-4 w-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>
                  </div>
                </div>
              </div>

              <!-- Message Textarea -->
              <div>
                <label class="block text-xs font-bold text-zinc-700 uppercase tracking-wider mb-2">Your Message</label>
                <textarea 
                  v-model="form.message"
                  required
                  rows="5"
                  placeholder="Tell us what you need help with..." 
                  class="w-full px-4 py-3 text-sm bg-stone-50 border border-zinc-200/70 rounded-xl focus:outline-none focus:bg-white focus:border-emerald-600 focus:ring-1 focus:ring-emerald-600 font-semibold text-zinc-900 placeholder-zinc-400 transition-all resize-y"
                ></textarea>
              </div>

              <!-- Submit Button -->
              <button 
                type="submit" 
                :disabled="isSubmitting"
                class="w-full py-4 px-6 bg-zinc-900 hover:bg-emerald-600 disabled:bg-zinc-400 text-white text-sm font-bold rounded-xl flex items-center justify-center gap-2 transition duration-300 shadow-md hover:shadow-emerald-600/20 group"
              >
                <span v-if="!isSubmitting">Send Message</span>
                <span v-else>Sending...</span>
                
                <svg v-if="!isSubmitting" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-4 h-4 group-hover:translate-x-1 transition-transform">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M6 12L3.269 3.126A59.768 59.768 0 0121.485 12 59.77 59.77 0 013.27 20.876L5.999 12zm0 0h7.5" />
                </svg>
                
                <!-- Loading Spinner -->
                <svg v-else class="animate-spin -ml-1 mr-3 h-4 w-4 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                  <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                  <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                </svg>
              </button>
              
              <p class="text-xs text-center text-zinc-500 font-medium">
                By submitting this form, you agree to our <a href="#" class="text-emerald-600 hover:underline">Privacy Policy</a>.
              </p>

            </form>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>