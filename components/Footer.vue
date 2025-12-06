<template>
  <footer class="bg-blue-600 text-white">
    <div class="max-w-5xl mx-auto px-6 py-12 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8 lg:gap-12">
        <!-- Brand Column -->
        <div class="space-y-4">
          <h3 class="text-white font-serif text-lg font-semibold">KPH</h3>
          <p class="text-sm text-white">
            Building Kerala's largest product community, one innovation at a time.
          </p>
          <div class="flex space-x-4">
            <a href="https://www.instagram.com/kerala.ph" target="_blank" class="hover:text-white">
              <Instagram class="h-5 w-5" />
            </a>
            <a href="https://x.com/keralaph" target="_blank" class="hover:text-white">
              <Twitter class="h-5 w-5" />
            </a>
            <a href="https://www.youtube.com/@FelixJosemonOfficial/videos" target="_blank" class="hover:text-white">
              <Youtube class="h-5 w-5" />
            </a>
            <a href="https://in.linkedin.com/company/keralaph" target="_blank" class="hover:text-white">
              <Linkedin class="h-5 w-5" />
            </a>
          </div>
        </div>

        <!-- Quick Links -->
        <div>
          <h3 class="text-white font-serif text-sm font-semibold mb-4">Quick Links</h3>
          <ul class="space-y-3 text-sm">
            <li><NuxtLink to="https://nas.io/kphjobs" target="_blank" rel="noopener noreferrer" class="hover:text-white">Jobs</NuxtLink></li>
            <li><NuxtLink to="https://wiki.kph.club" target="_blank" rel="noopener noreferrer" class="hover:text-white">Wiki</NuxtLink></li>
            <li><NuxtLink to="https://blog.kph.club" target="_blank" rel="noopener noreferrer" class="hover:text-white">Blog</NuxtLink></li>
          </ul>
        </div>

        <!-- Resources -->
        <div>
          <h3 class="text-white font-serif text-sm font-semibold mb-4">Resources</h3>
          <ul class="space-y-3 text-sm">
            <li><a href="https://wiki.kph.club" class="hover:text-white">Startup Wiki</a></li>
            <li><a href="https://www.youtube.com/@FelixJosemonOfficial/videos" class="hover:text-white">Podcasts</a></li>
            <li><a href="https://learn.kph.club" target="_blank" rel="noopener noreferrer" class="hover:text-white">Masterclass</a></li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div class="mt-12 pt-8">
        <div class="flex flex-col md:flex-row justify-between items-center gap-4">
          <p class="text-sm text-white">
             © {{ new Date().getFullYear() }} KPH. All rights reserved.
           </p>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { Instagram, Twitter, Youtube, MessageCircle, Linkedin } from 'lucide-vue-next'
</script> 