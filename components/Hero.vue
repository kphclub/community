<template>
  <div class="bg-white py-16 sm:py-18">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="mx-auto max-w-2xl sm:max-w-3xl text-center">
        <Motion
          :initial="{ opacity: 0, y: 30 }"
          :animate="{ opacity: 1, y: 0 }"
          :transition="{ duration: 0.6, ease: 'easeOut' }"
        >
          <h1 class="text-5xl font-bold tracking-tight text-gray-900 sm:text-7xl">
            Kerala's #1
            <span class="bg-blue-100 text-blue-600 px-3 py-1 rounded-lg inline-block transform -rotate-1">
              Startup Community
            </span>
          </h1>
        </Motion>

        <Motion
          :initial="{ opacity: 0, y: 20 }"
          :animate="{ opacity: 1, y: 0 }"
          :transition="{ duration: 0.6, delay: 0.2, ease: 'easeOut' }"
        >
          <p class="mt-8 text-xl leading-8 text-gray-600">
            Join Kerala's most powerful network of builders, entrepreneurs and
            innovators building the next big thing.
          </p>
        </Motion>

        <Motion
          :initial="{ opacity: 0, y: 20 }"
          :animate="{ opacity: 1, y: 0 }"
          :transition="{ duration: 0.6, delay: 0.4, ease: 'easeOut' }"
        >
          <div class="mt-8">
            <Motion
              as="a"
              href="https://nas.io/kph"
              target="_blank"
              rel="noopener noreferrer"
              :whileHover="{ scale: 1.02 }"
              :whileTap="{ scale: 0.98 }"
              class="group inline-flex items-center justify-center gap-3 rounded-lg bg-blue-600 px-8 py-3 text-lg font-medium text-white hover:bg-blue-700 transition-colors duration-300"
            >
              Join KPH
              <ArrowRight class="w-5 h-5 group-hover:translate-x-1 transition-transform" />
            </Motion>
            <p class="mt-4 text-sm text-gray-500">
              Join 1000+ founders building Kerala's next generation of startups
            </p>
          </div>
        </Motion>
      </div>
    </div>
  </div>
</template>

<script setup>
import { Motion } from "motion-v";
import { ArrowRight } from "lucide-vue-next";
</script>
