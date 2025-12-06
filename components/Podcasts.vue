<template>
  <!-- Reduce section padding -->
  <section class="py-16 sm:py-18 bg-white">
    <div class="max-w-5xl mx-auto px-6 lg:px-8">
      <!-- Header -->
      <div class="flex items-center justify-between mb-12">
        <div>
          <div class="inline-block bg-blue-100 px-4 py-2 rounded-lg mb-4">
            <h2
              class="text-3xl font-bold tracking-tight text-blue-600 sm:text-4xl"
            >
              Learn from the best
            </h2>
          </div>
          <p class="mt-4 text-lg leading-8 text-gray-600">
            Insights, Stories, and Lessons from Kerala's Top Innovators.
          </p>
        </div>
        <a
          href="https://www.youtube.com/@FelixJosemonOfficial/videos"
          target="_blank"
          rel="noopener noreferrer"
          class="group inline-flex items-center gap-2 text-blue-600 hover:text-blue-800 font-medium transition-colors duration-200 whitespace-nowrap"
        >
          <span>View all podcasts</span>
          <ArrowUpRight
            class="h-4 w-4 group-hover:translate-x-0.5 group-hover:-translate-y-0.5 transition-transform"
          />
        </a>
      </div>

      <!-- Podcast Grid -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-12">
        <div
          v-for="podcast in podcasts"
          :key="podcast.id"
          class="group opacity-0 animate-slide-up"
          :style="`animation-delay: ${podcast.id * 100}ms`"
        >
          <a
            :href="`https://www.youtube.com/watch?v=${podcast.videoId}`"
            target="_blank"
            class="block transform-gpu hover:-translate-y-1 transition-all duration-300"
          >
            <div
              class="aspect-video overflow-hidden rounded-xl border group-hover:border-red-200 transition-colors"
            >
              <div class="relative">
                <img
                  :src="`https://img.youtube.com/vi/${podcast.videoId}/maxresdefault.jpg`"
                  :alt="podcast.title"
                  class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
                />
                <!-- Play button overlay -->
                <div
                  class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300"
                >
                  <div
                    class="bg-black/75 p-4 rounded-full transform-gpu scale-75 group-hover:scale-100 transition-transform"
                  >
                    <Play class="w-8 h-8 text-white" />
                  </div>
                </div>
              </div>
            </div>
            <div class="mt-6 p-4 border rounded-lg">
              <h3
                class="text-xl font-semibold text-gray-900 group-hover:text-gray-700"
              >
                {{ podcast.title }}
              </h3>
              <p class="mt-2 text-sm text-gray-600">{{ podcast.guest }}</p>
            </div>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Youtube, Play, ArrowUpRight } from "lucide-vue-next";

// Sample podcast data - replace videoIds with actual YouTube video IDs
const podcasts = [
  {
    id: 1,
    videoId: "mfQezc7jd_4",
    title: "The Truth About AI in Tech",
    guest: "Kailash Nadh, CTO of Zerodha",
  },
  {
    id: 2,
    videoId: "3y-iQiVk8fw",
    title: "Kerala is waiting for next Zoho!",
    guest: "Arjun Pillai, Founder of Docket",
  },
  {
    id: 3,
    videoId: "yjUQ6aTpYeE",
    title: "Malayali Backing 240+ Founders Worldwide",
    guest: "Shibin Dotco, Partner Y0",
  },
  {
    id: 4,
    videoId: "aOIkW862jGU",
    title: "From Kerala to Y Combinator",
    guest: "Mufeed VH, Founder of Winfunc",
  },
  {
    id: 5,
    videoId: "_y4kQ2ILDdM",
    title: "Helping Millions in India to be Job-Ready",
    guest: "Mohammed Hisamuddin, CEO of Entri",
  },
  {
    id: 6,
    videoId: "ZfMPSVKWAgc",
    title: "Xylem Strategy for NEET Crackers",
    guest: "Dr. Ananthu, CEO of Xylem Learning ",
  },
];
</script>

<style scoped>
@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-slide-up {
  animation: slideUp 0.6s ease-out forwards;
}
</style>
