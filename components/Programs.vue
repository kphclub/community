<template>
  <section class="py-16 sm:py-18 bg-blue-600">
    <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Header -->
      <div class="text-left mb-12">
        <h2 class="text-3xl font-bold tracking-tight text-white sm:text-4xl mb-4">
          Join KPH
        </h2>
        <p class="mt-4 text-lg leading-8 text-blue-100 max-w-2xl">
          Join Kerala's largest product community. Network &amp; grow together.
        </p>
      </div>

      <!-- Main Content -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        <!-- Left: Email signup -->
        <div>
          <input
            type="email"
            placeholder="Enter your email"
            class="w-full rounded-lg border border-white bg-white px-4 py-3 text-gray-900 placeholder-gray-500 focus:border-blue-300 focus:outline-none focus:ring-2 focus:ring-blue-300 mb-3"
          />
          <button
            class="group w-full flex items-center justify-center gap-3 rounded-lg bg-white px-8 py-3 text-lg font-medium text-blue-600 hover:bg-blue-50 transition-all duration-300"
          >
            Join
          </button>
        </div>

        <!-- Right: Features as bullets -->
        <div class="space-y-4">
          <div class="flex gap-3 items-center">
            <Users class="h-5 w-5 text-white flex-shrink-0" />
            <h3 class="font-semibold text-white">Community</h3>
          </div>
          <div class="flex gap-3 items-center">
            <Rocket class="h-5 w-5 text-white flex-shrink-0" />
            <h3 class="font-semibold text-white">Builder Accelerator</h3>
          </div>
          <div class="flex gap-3 items-center">
            <Wallet class="h-5 w-5 text-white flex-shrink-0" />
            <h3 class="font-semibold text-white">Investor Network</h3>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Users, Rocket, Wallet, ArrowRight } from 'lucide-vue-next'
</script> 