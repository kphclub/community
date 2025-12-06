<template>
  <!-- Clean white for hero section -->
  <div class="bg-white py-16 sm:py-18">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl text-center">
        <!-- Animated title with staggered fade-in -->
        <h1 
          class="text-5xl font-bold tracking-tight text-gray-900 sm:text-7xl opacity-0 animate-fade-in"
        >
          Every Product happening in 
          <span class="bg-emerald-100 text-emerald-600 px-3 py-1 rounded-lg inline-block transform -rotate-1">Kerala</span> 🌴
        </h1>
        <!-- Animated subtitle with delay -->
        <p 
          class="mt-8 text-xl leading-8 text-gray-600 opacity-0 animate-fade-in animation-delay-200"
        >
          Join Kerala's most powerful network of builders, entrepreneurs and innovators building the next big thing.
        </p>
        <!-- Button with hover effect -->
        <div class="mt-8">
          <a href="http://nas.io/kph" target="_blank" rel="noopener noreferrer" 
            class="group inline-flex items-center gap-3 rounded-lg bg-black px-8 py-4 text-lg font-semibold text-white hover:bg-gray-900 transition-all duration-300"
          >
            Request an Invite
            <ArrowRight class="h-5 w-5 group-hover:translate-x-1 transition-transform" />
        </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ArrowRight } from 'lucide-vue-next'
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