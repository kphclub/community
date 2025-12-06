<template>
  <!-- Clean white for hero section -->
  <div class="bg-white py-16 sm:py-18">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="mx-auto max-w-2xl sm:max-w-3xl text-center">
        <!-- Animated title with staggered fade-in -->
        <h1
          class="text-5xl font-bold tracking-tight text-gray-900 sm:text-7xl opacity-0 animate-fade-in"
        >
          Kerala's #1
          <span
            class="bg-blue-100 text-blue-600 px-3 py-1 rounded-lg inline-block transform -rotate-1"
            >Startup Community</span
          >
        </h1>
        <!-- Animated subtitle with delay -->
        <p
          class="mt-8 text-xl leading-8 text-gray-600 opacity-0 animate-fade-in animation-delay-200"
        >
          Join Kerala's most powerful network of builders, entrepreneurs and
          innovators building the next big thing.
        </p>
        <!-- Email input field -->
        <div class="mt-8">
          <div class="flex flex-col sm:flex-row gap-3">
            <input
              type="email"
              placeholder="Enter your email"
              class="flex-1 rounded-lg border border-gray-300 bg-white px-4 py-3 text-gray-900 placeholder-gray-500 focus:border-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
            <button
              class="group inline-flex items-center justify-center sm:justify-start gap-3 rounded-lg bg-blue-600 px-8 py-3 text-lg font-medium text-white hover:bg-blue-700 transition-all duration-300 whitespace-nowrap"
            >
              Join KPH
              <ArrowRight
                class="w-5 h-5 group-hover:translate-x-1 transition-transform"
              />
            </button>
          </div>
          <p class="mt-4 text-sm text-gray-500">
            Join 1000+ founders building Kerala's next generation of startups
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ArrowRight } from "lucide-vue-next";
</script>

<style scoped>
@keyframes fadeIn {
  0% {
    opacity: 0;
    transform: translateY(20px) scale(0.95);
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

.animate-fade-in {
  animation: fadeIn 0.8s cubic-bezier(0.2, 0.8, 0.2, 1) forwards;
}

.animation-delay-200 {
  animation-delay: 200ms;
}
</style>
