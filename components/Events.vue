<template>
  <section class="py-16 sm:py-18 bg-blue-600">
    <div class="max-w-5xl mx-auto px-6 lg:px-8">
      <!-- Header -->
      <Motion
        :initial="{ opacity: 0, y: 20 }"
        :inView="{ opacity: 1, y: 0 }"
        :transition="{ duration: 0.5 }"
      >
        <div class="text-center max-w-2xl mx-auto mb-12">
          <h2 class="text-3xl font-bold tracking-tight text-white sm:text-4xl">
            Join the movement of creators, dreamers, and doers from Kerala
          </h2>
          <p class="mt-4 text-lg leading-8 text-blue-100">
            We host invite-only meet-ups to accelerate turning bold ideas into successful products.
          </p>
        </div>
      </Motion>

      <!-- Events Grid -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-12">
        <Motion
          v-for="(event, index) in events"
          :key="event.id"
          :initial="{ opacity: 0, y: 30 }"
          :inView="{ opacity: 1, y: 0 }"
          :transition="{ duration: 0.5, delay: index * 0.1 }"
          :whileHover="{ y: -5 }"
          class="group relative aspect-square overflow-hidden rounded-lg cursor-pointer"
        >
          <img 
            :src="event.image"
            :alt="event.title"
            class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
          />
          <div class="absolute inset-0 bg-blue-600/0 group-hover:bg-blue-600/60 transition-colors duration-300 flex flex-col justify-end p-4 opacity-0 group-hover:opacity-100 transition-opacity duration-300">
            <h3 class="text-xl font-semibold text-white">
              {{ event.title }}
            </h3>
            <p class="mt-2 text-sm text-blue-100">{{ event.description }}</p>
            <div class="flex gap-2 mt-3">
              <div class="bg-white px-2.5 py-1 rounded-md">
                <time class="text-xs font-medium text-blue-600">{{ event.date }}</time>
              </div>
              <div class="bg-white px-2.5 py-1 rounded-md">
                <span class="text-xs font-medium text-blue-600">{{ event.location }}</span>
              </div>
            </div>
          </div>
        </Motion>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Motion } from 'motion-v'
import { CalendarDays, ArrowRight } from 'lucide-vue-next'

const events = [
  {
    id: 1,
    title: "KPH Kochi Meetup",
    date: "February 2024",
    location: "Kochi",
    description: "A day of networking and knowledge sharing with Kerala's top product builders.",
    image: "/events/kochi-meetup.jpeg"
  },
  {
    id: 2,
    title: "KPH San Francisco Meetup",
    date: "May 2024",
    location: "San Francisco",
    description: "Connect with Kerala founders building for the global market in Silicon Valley.",
    image: "/events/sf-meetup.jpeg"
  },
  {
    id: 3,
    title: "KPH Toronto Ecommerce Meetup",
    date: "May 2024",
    location: "Toronto",
    description: "Special focus on ecommerce innovations and cross-border commerce strategies.",
    image: "/events/toronto-meetup.jpeg"
  }
]
</script> 