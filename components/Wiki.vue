<template>
  <!-- Reduce section padding -->
  <section class="py-16 sm:py-18 bg-white">
    <div class="max-w-5xl mx-auto px-6 lg:px-8">
      <!-- Header -->
      <div class="flex items-center justify-between mb-12">
        <div>
          <div class="inline-block bg-blue-100 px-4 py-2 rounded-lg mb-4">
            <h2 class="text-3xl font-bold tracking-tight text-blue-600 sm:text-4xl">
              Knowledge Base
            </h2>
          </div>
          <p class="mt-4 text-lg leading-8 text-gray-600">
            Discover insights, journeys, and lessons from creators and innovators.
          </p>
        </div>
        <a 
          href="https://wiki.kph.club"
          target="_blank"
          rel="noopener noreferrer"
          class="group inline-flex items-center gap-2 text-blue-600 hover:text-blue-800 font-medium transition-colors duration-200 whitespace-nowrap"
        >
          <span>Explore wiki</span>
          <ArrowRight class="h-4 w-4 group-hover:translate-x-1 transition-transform" />
        </a>
      </div>

      <!-- Wiki Articles -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-12">
        <article v-for="(article, index) in articles" :key="article.id"
          class="relative group bg-white rounded-xl border p-5 hover:shadow-sm transition-all duration-300 opacity-0 animate-slide-in"
          :style="`animation-delay: ${index * 150}ms`"
        >
          <div class="flex items-start gap-4">
            <div class="flex-shrink-0 mt-1 transform-gpu group-hover:rotate-12 transition-transform duration-300">
              <CreditCard class="h-6 w-6 text-emerald-600" />
            </div>
            <div class="flex-1">
              <div class="flex gap-2 mb-3">
                <div class="bg-blue-100 px-2.5 py-1 rounded-md">
                  <span class="text-sm font-medium text-blue-700">Guide</span>
                </div>
                <div class="bg-amber-100 px-2.5 py-1 rounded-md">
                  <span class="text-sm font-medium text-amber-700">2 min read</span>
                </div>
              </div>
              <h3 class="text-xl font-semibold text-gray-900 group-hover:text-gray-700">
                <a :href="article.url" target="_blank" class="stretched-link">
                  {{ article.title }}
                </a>
              </h3>
              <p class="mt-2 text-sm text-gray-600">
                {{ article.description }}
              </p>
            </div>
          </div>

        </article>
      </div>


    </div>
  </section>
</template>

<script setup>
import { BookOpen, CreditCard, ArrowRight } from 'lucide-vue-next'

const articles = [
  {
    id: 1,
    title: "Accepting International Payments Without Company Registration",
    description: "Learn about payment gateways, tax compliance, and legal considerations for early-stage startups.",
    url: "https://wiki.kph.club/accepting-international-payments-without-company-registration"
  },
  {
    id: 2,
    title: "How to Register a Delaware C-Corporation",
    description: "A structured approach to registering a Delaware C Corporation for founders with different financial arrangements.",
    url: "https://wiki.kph.club/how-to-register-a-delaware-c-corporation"
  }
]
</script>

<style scoped>
@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-slide-in {
  animation: slideIn 0.5s ease-out forwards;
}
</style> 