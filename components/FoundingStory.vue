<template>
  <!-- Reduce section padding -->
  <section class="py-16 sm:py-18 bg-white">
    <div class="max-w-5xl mx-auto px-6 lg:px-8">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-16 items-center">
         <!-- Image container -->
         <div
           class="relative h-[250px] sm:h-[300px] lg:h-[350px] rounded-xl overflow-hidden border shadow-sm"
         >
          <img
            src="/felix-josemon.jpg"
            alt="Felix Josemon, founder of KPH"
            class="absolute inset-0 w-full h-full object-cover"
          />
        </div>

        <!-- Story content -->
        <div class="space-y-6">
          <div class="inline-block bg-blue-100 px-4 py-2 rounded-lg">
            <h2
              class="text-3xl font-bold tracking-tight text-blue-600 sm:text-4xl"
            >
              Our Founding Story
            </h2>
          </div>
          <div class="text-lg leading-8 text-gray-600 space-y-6">
            <p>
              Founded in 2017 by Felix Josemon, KPH started as a WhatsApp group for like-minded builders in Kerala.
            </p>
            <p>
              Today, it's an exclusive community of 1,000+ founders building impactful internet products, connecting in-person, and sharing knowledge.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ArrowRight } from "lucide-vue-next";
</script>
