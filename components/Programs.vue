<template>
  <section class="py-16 sm:py-18 bg-blue-600">
    <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Header -->
      <Motion
        :initial="{ opacity: 0, y: 20 }"
        :inView="{ opacity: 1, y: 0 }"
        :transition="{ duration: 0.5 }"
      >
        <div class="text-left mb-12">
          <h2 class="text-3xl font-bold tracking-tight text-white sm:text-4xl mb-4">
            Join KPH
          </h2>
          <p class="mt-4 text-lg leading-8 text-blue-100 max-w-2xl">
            Join Kerala's largest product community. Network &amp; grow together.
          </p>
        </div>
      </Motion>

      <!-- Main Content -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-12">
        <!-- Left: Join button -->
        <Motion
          :initial="{ opacity: 0, x: -20 }"
          :inView="{ opacity: 1, x: 0 }"
          :transition="{ duration: 0.5, delay: 0.2 }"
        >
          <Motion
            as="a"
            href="https://nas.io/kph"
            target="_blank"
            rel="noopener noreferrer"
            :whileHover="{ scale: 1.02 }"
            :whileTap="{ scale: 0.98 }"
            class="group inline-flex items-center justify-center gap-3 rounded-lg bg-white px-8 py-3 text-lg font-medium text-blue-600 hover:bg-blue-50 transition-colors duration-300"
          >
            Join KPH
            <ArrowRight class="w-5 h-5 group-hover:translate-x-1 transition-transform" />
          </Motion>
        </Motion>

        <!-- Right: Features as bullets -->
        <div class="space-y-4 flex flex-col items-center lg:items-end">
          <Motion
            v-for="(feature, index) in features"
            :key="feature.label"
            :initial="{ opacity: 0, x: 20 }"
            :inView="{ opacity: 1, x: 0 }"
            :transition="{ duration: 0.4, delay: 0.3 + index * 0.1 }"
            class="flex gap-3 items-center"
          >
            <component :is="feature.icon" class="h-5 w-5 text-white flex-shrink-0" />
            <h3 class="font-semibold text-white">{{ feature.label }}</h3>
          </Motion>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Motion } from 'motion-v'
import { Users, Rocket, Wallet, ArrowRight } from 'lucide-vue-next'

const features = [
  { icon: Users, label: 'Community' },
  { icon: Rocket, label: 'Builder Accelerator' },
  { icon: Wallet, label: 'Investor Network' },
]
</script> 