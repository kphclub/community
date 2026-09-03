<template>
  <div class="min-h-screen bg-[#030306] text-neutral-100 selection:bg-purple-600 selection:text-white font-sans relative overflow-x-hidden">
    <!-- FUTURISTIC PAGE PRELOADER OVERLAY -->
    <div
      :class="[
        'fixed inset-0 z-[100] bg-[#030306] flex flex-col items-center justify-center p-4 transition-all duration-700 ease-in-out',
        isLoading ? 'opacity-100 scale-100 pointer-events-auto' : 'opacity-0 scale-105 pointer-events-none'
      ]"
    >
      <!-- Background Ambient Glow -->
      <div class="absolute w-80 h-80 rounded-full bg-purple-600/20 blur-3xl animate-pulse"></div>

      <!-- Preloader Graphic & Spinner -->
      <div class="relative z-10 flex flex-col items-center max-w-md text-center">
        <div class="relative flex items-center justify-center w-20 h-20 mb-4">
          <!-- Outer Rotating Gradient Ring -->
          <div class="absolute inset-0 rounded-full border-2 border-transparent border-t-purple-400 border-r-pink-400 animate-spin"></div>
          <!-- Inner Reverse Rotating Cyan Ring -->
          <div class="absolute inset-2 rounded-full border-2 border-transparent border-b-cyan-400 animate-spin-reverse opacity-80"></div>
          
          <!-- Logo Image -->
          <img
            alt="KPH Loading"
            class="h-8 w-auto object-contain drop-shadow-[0_0_12px_rgba(168,85,247,0.8)] animate-pulse"
          />
        </div>

        <!-- Animated Text -->
        <span class="font-chakra-bold font-bold text-2xl tracking-wider text-white mb-3">
          KPH<span class="text-purple-400">.</span>hack
        </span>

        <!-- CLEAN ANIMATED BUILDER QUOTE CARD -->
        <div class="w-full bg-[#0c0b1a]/80 border border-purple-500/25 rounded-2xl p-5 mb-5 backdrop-blur-xl shadow-[0_0_30px_rgba(168,85,247,0.15)] relative overflow-hidden transition-all duration-500">
          <div class="absolute top-2 left-3 opacity-20 text-purple-400">
            <Quote class="w-5 h-5 rotate-180" />
          </div>
          <div class="relative z-10 py-0.5 px-2">
            <p :key="`quote-${currentQuoteIndex}`" class="text-sm sm:text-base font-medium italic text-neutral-200 leading-relaxed animate-quote-fade">
              "{{ currentQuote.text }}"
            </p>
            <span :key="`author-${currentQuoteIndex}`" class="block mt-2.5 text-xs font-mono font-bold text-purple-300 tracking-wider uppercase animate-quote-fade">
              — {{ currentQuote.author }}
            </span>
          </div>
        </div>

        <!-- Percentage Counter Bar -->
        <div class="w-56 h-1.5 bg-white/10 rounded-full overflow-hidden mb-3">
          <div
            class="h-full bg-gradient-to-r from-purple-500 via-pink-500 to-cyan-400 transition-all duration-300 rounded-full shadow-[0_0_12px_rgba(168,85,247,0.8)]"
            :style="{ width: `${progress}%` }"
          ></div>
        </div>

        <div class="flex items-center gap-2 font-mono text-xs text-purple-300 tracking-widest uppercase">
          <Sparkles class="w-3.5 h-3.5 text-pink-400 animate-spin-slow" />
          <span>PREPARING HACKATHON • {{ progress }}%</span>
        </div>
      </div>
    </div>

    <!-- QINTARA STYLE FLOATING CAPSULE NAVBAR -->
    <header class="fixed top-5 left-1/2 -translate-x-1/2 z-50 w-[94%] max-w-6xl flex items-center justify-between pointer-events-auto">
      <!-- Brand Logo -->
      <NuxtLink to="/" class="flex items-center gap-2 group">
        <img
          src="/kph-main-logo.png"
          alt="KPH.CLUB"
          class="h-7 w-auto object-contain transition-transform group-hover:scale-105 drop-shadow-[0_0_10px_rgba(255,255,255,0.3)]"
        />
        <span class="font-chakra-bold font-bold text-lg text-white group-hover:text-purple-300 transition-colors">
          KPH<span class="text-purple-400">.</span>HACK
        </span>
      </NuxtLink>

      <!-- Center Pill Nav Menu -->
      <nav class="hidden md:flex items-center gap-7 bg-[#0c0b16]/80 backdrop-blur-xl border border-white/10 rounded-full px-8 py-2.5 shadow-[0_8px_30px_rgba(0,0,0,0.8)] text-xs font-mono text-neutral-300">
        <a href="#about" class="hover:text-white transition-colors">Why Join</a>
        <a href="#highlights" class="hover:text-white transition-colors">Previous Hackathons</a>      </nav>

      <!-- Right Pill CTA Button -->
      <a
        href="https://docs.google.com/forms/d/e/1FAIpQLSdvMpY7b3fyYfLEwgE20EqKSGD9vnm4fbYMOwCmlLVjyGUYTw/viewform?usp=publish-editor"
        target="_blank"
        rel="noopener noreferrer"
        class="bg-white text-black font-semibold text-xs px-5 py-2.5 rounded-full hover:bg-neutral-200 transition-all duration-300 shadow-md hover:scale-105 flex items-center gap-2"
      >
        <span>JOIN NOW</span>
        <ArrowRight class="h-3.5 w-3.5" />
      </a>
    </header>

    <!-- PRIMARY HERO SECTION (Interactive & High-Energy Hero Space) -->
    <section
      @mousemove="handleMouseMove"
      class="relative min-h-[92vh] bg-[#030306] text-white flex flex-col items-center justify-between pt-32 pb-0 overflow-hidden"
    >
      <!-- Primary Space Animated GIF Background Overlay -->
      <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none">
        <img
          src="/pri-sp-vid.gif"
          alt="Primary Space Background"
          class="w-full h-full object-cover object-center opacity-40 mix-blend-screen transform scale-105"
        />
        <div class="absolute inset-0 bg-gradient-to-b from-[#030306]/90 via-[#030306]/50 to-[#030306]"></div>
      </div>

      <!-- Interactive Dynamic Mouse-Glow & Ambient Beams -->
      <div
        class="absolute inset-0 pointer-events-none overflow-hidden z-0 transition-transform duration-300 ease-out"
        :style="{ transform: `translate3d(${mouseX}px, ${mouseY}px, 0)` }"
      >
        <div class="absolute top-1/4 left-1/2 -translate-x-1/2 w-[800px] h-[550px] rounded-full bg-gradient-to-tr from-purple-600/20 via-pink-500/20 to-cyan-400/20 blur-[170px] animate-pulse"></div>
        <div class="absolute bottom-12 left-1/4 w-[450px] h-[320px] rounded-full bg-purple-600/15 blur-[150px]"></div>
        <div class="absolute bottom-12 right-1/4 w-[450px] h-[320px] rounded-full bg-cyan-600/15 blur-[150px]"></div>
      </div>

      <!-- 3D Perspective Grid at Base -->
      <div class="absolute bottom-0 left-1/2 -translate-x-1/2 w-[160%] h-64 pointer-events-none opacity-20 bg-[linear-gradient(to_right,#3b0764_1px,transparent_1px),linear-gradient(to_bottom,#3b0764_1px,transparent_1px)] bg-[size:3.5rem_3.5rem] [transform:perspective(500px)_rotateX(60deg)] z-0"></div>

      <!-- Hero Main Interactive Content -->
      <div class="relative z-10 max-w-5xl mx-auto px-4 text-center flex flex-col items-center my-auto pt-4 pb-8">
        <!-- Live Status Badge -->
        <div class="inline-flex items-center gap-2.5 px-4 py-2 rounded-full bg-[#0d0c1d]/90 border border-purple-500/40 backdrop-blur-xl mb-6 shadow-[0_0_20px_rgba(168,85,247,0.2)] animate-fade-in-up hover:border-purple-400 transition-colors">
          <span class="w-2.5 h-2.5 rounded-full bg-emerald-400 animate-ping"></span>
          <span class="text-xs font-mono font-bold tracking-widest text-purple-200 uppercase">
            REGISTRATION OPEN • OCTOBER 3,4 2026
          </span>
        </div>

        <!-- Main Title -->
        <h1 class="text-5xl sm:text-7xl lg:text-8xl xl:text-9xl font-chakra-bold font-bold tracking-tight text-white max-w-5xl leading-[0.95] animate-title-glow drop-shadow-[0_10px_35px_rgba(0,0,0,0.8)]">
          KPH Hackathon'26
        </h1>
        
        <!-- Subtitle -->
        <h5 class="block mt-4 text-2xl sm:text-4xl lg:text-5xl font-chakra-bold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-purple-300 via-pink-300 to-cyan-300 animate-subtitle-glow drop-shadow-[0_5px_20px_rgba(168,85,247,0.5)]">
          Build.Launch.Scale
        </h5>

        <!-- FUTURISTIC HERO COUNTDOWN TIMER (OCTOBER 3 2026) -->
        <div class="mt-8 mb-2 w-full max-w-xl mx-auto">
          <div class="relative group">
            <!-- Glowing background aura -->
            <div class="absolute -inset-0.5 bg-gradient-to-r from-purple-600 via-pink-600 to-cyan-500 rounded-3xl blur opacity-35 group-hover:opacity-75 transition duration-500"></div>
            
            <div class="relative bg-[#090816]/90 border border-purple-500/30 backdrop-blur-xl rounded-2xl sm:rounded-3xl p-5 sm:p-6 shadow-[0_10px_40px_rgba(0,0,0,0.8)]">
              <!-- Header Label -->
              <div class="flex items-center justify-center gap-2 mb-4 text-xs font-mono font-bold tracking-[0.2em] text-purple-300 uppercase">
                <Clock class="w-4 h-4 text-pink-400 animate-pulse" />
                <span>HACKATHON STARTS IN</span>
                <Flame class="w-4 h-4 text-amber-400 animate-pulse" />
              </div>

              <!-- 4 Counter Grid Blocks -->
              <div class="grid grid-cols-4 gap-2.5 sm:gap-4">
                <!-- Days -->
                <div class="flex flex-col items-center justify-center bg-white/[0.04] border border-white/10 rounded-xl sm:rounded-2xl p-2.5 sm:p-4 hover:border-purple-500/50 hover:bg-purple-950/30 transition-all">
                  <span class="font-chakra-bold font-bold text-3xl sm:text-5xl text-white tracking-tight drop-shadow-[0_0_15px_rgba(168,85,247,0.6)]">
                    {{ timeLeft.days }}
                  </span>
                  <span class="text-[10px] sm:text-xs font-mono font-bold tracking-widest text-purple-300/80 uppercase mt-1">
                    Days
                  </span>
                </div>

                <!-- Hours -->
                <div class="flex flex-col items-center justify-center bg-white/[0.04] border border-white/10 rounded-xl sm:rounded-2xl p-2.5 sm:p-4 hover:border-pink-500/50 hover:bg-pink-950/30 transition-all">
                  <span class="font-chakra-bold font-bold text-3xl sm:text-5xl text-white tracking-tight drop-shadow-[0_0_15px_rgba(236,72,153,0.6)]">
                    {{ timeLeft.hours }}
                  </span>
                  <span class="text-[10px] sm:text-xs font-mono font-bold tracking-widest text-pink-300/80 uppercase mt-1">
                    Hours
                  </span>
                </div>

                <!-- Minutes -->
                <div class="flex flex-col items-center justify-center bg-white/[0.04] border border-white/10 rounded-xl sm:rounded-2xl p-2.5 sm:p-4 hover:border-cyan-500/50 hover:bg-cyan-950/30 transition-all">
                  <span class="font-chakra-bold font-bold text-3xl sm:text-5xl text-white tracking-tight drop-shadow-[0_0_15px_rgba(6,182,212,0.6)]">
                    {{ timeLeft.minutes }}
                  </span>
                  <span class="text-[10px] sm:text-xs font-mono font-bold tracking-widest text-cyan-300/80 uppercase mt-1">
                    Mins
                  </span>
                </div>

                <!-- Seconds -->
                <div class="flex flex-col items-center justify-center bg-white/[0.04] border border-white/10 rounded-xl sm:rounded-2xl p-2.5 sm:p-4 hover:border-amber-500/50 hover:bg-amber-950/30 transition-all">
                  <span class="font-chakra-bold font-bold text-3xl sm:text-5xl text-purple-300 tracking-tight drop-shadow-[0_0_15px_rgba(168,85,247,0.8)] animate-pulse">
                    {{ timeLeft.seconds }}
                  </span>
                  <span class="text-[10px] sm:text-xs font-mono font-bold tracking-widest text-purple-300 uppercase mt-1">
                    Secs
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>



        <!-- DUAL CTAS (JOIN NOW + WHY JOIN) -->
        <div class="mt-8 flex flex-wrap items-center justify-center gap-4">
          <a
            href="https://docs.google.com/forms/d/e/1FAIpQLSdvMpY7b3fyYfLEwgE20EqKSGD9vnm4fbYMOwCmlLVjyGUYTw/viewform?usp=publish-editor"
            target="_blank"
            rel="noopener noreferrer"
            class="group inline-flex items-center gap-3 rounded-full bg-white px-9 py-4 text-base font-bold text-gray-950 hover:bg-neutral-200 hover:scale-105 transition-all duration-300 shadow-[0_0_35px_rgba(255,255,255,0.3)]"
          >
            <span>JOIN NOW</span>
            <ArrowRight class="h-4 w-4 group-hover:translate-x-1.5 transition-transform" />
          </a>

          <a
            href="#about"
            class="inline-flex items-center gap-2.5 rounded-full bg-[#121026]/90 border border-purple-500/30 px-7 py-4 text-base font-semibold text-purple-200 hover:text-white hover:border-purple-400 hover:bg-purple-950/50 hover:scale-105 transition-all duration-300 backdrop-blur-xl"
          >
            <Trophy class="h-4 w-4 text-purple-400" />
            <span>Why Join</span>
          </a>
        </div>
        <p class="mt-4 text-xs font-medium text-purple-300/90 tracking-wide">
          Hurry up, spots are limited!
        </p>
      </div>

      <!-- MINIMAL PROFESSIONAL TICKER MARQUEE EMBEDDED DIRECTLY IN PRIMARY HERO -->
      <div class="relative w-full bg-[#060512]/85 border-t border-white/10 py-3.5 overflow-hidden backdrop-blur-xl z-20 shadow-[0_-4px_25px_rgba(0,0,0,0.4)]">
        <!-- Gradient Edge Fades -->
        <div class="pointer-events-none absolute inset-y-0 left-0 w-28 bg-gradient-to-r from-[#030306] to-transparent z-10"></div>
        <div class="pointer-events-none absolute inset-y-0 right-0 w-28 bg-gradient-to-l from-[#030306] to-transparent z-10"></div>

        <div class="flex whitespace-nowrap animate-marquee">
          <!-- Marquee Items - Group 1 -->
          <div class="flex items-center gap-10 sm:gap-16 shrink-0 pr-10 sm:pr-16 text-xs sm:text-sm font-chakra-bold tracking-[0.25em] uppercase text-white/90">
            <span class="flex items-center gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-purple-400"></span>
              OCTOBER 3,4 2026
            </span>
            <span class="text-purple-500/40">✦</span>
            <span class="flex items-center gap-3 text-purple-300">
              <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-ping"></span>
              REGISTRATION OPEN
            </span>
            <span class="text-purple-500/40">✦</span>
            <span class="flex items-center gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-purple-400"></span>
              OCTOBER 3,4 2026
            </span>
            <span class="text-purple-500/40">✦</span>
            <span class="flex items-center gap-3 text-purple-300">
              <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-ping"></span>
              REGISTRATION OPEN
            </span>
            <span class="text-purple-500/40">✦</span>
          </div>

          <!-- Marquee Items - Group 2 (Duplicate for Seamless Loop) -->
          <div class="flex items-center gap-10 sm:gap-16 shrink-0 pr-10 sm:pr-16 text-xs sm:text-sm font-chakra-bold tracking-[0.25em] uppercase text-white/90" aria-hidden="true">
            <span class="flex items-center gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-purple-400"></span>
              OCTOBER 3,4 2026
            </span>
            <span class="text-purple-500/40">✦</span>
            <span class="flex items-center gap-3 text-purple-300">
              <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-ping"></span>
              REGISTRATION OPEN
            </span>
            <span class="text-purple-500/40">✦</span>
            <span class="flex items-center gap-3">
              <span class="w-1.5 h-1.5 rounded-full bg-purple-400"></span>
              OCTOBER 3,4 2026
            </span>
            <span class="text-purple-500/40">✦</span>
            <span class="flex items-center gap-3 text-purple-300">
              <span class="w-1.5 h-1.5 rounded-full bg-emerald-400 animate-ping"></span>
              REGISTRATION OPEN
            </span>
            <span class="text-purple-500/40">✦</span>
          </div>
        </div>
      </div>
    </section>

    <!-- WHY KPH HACKATHON SECTION (Chakra Petch Bold Title) -->
    <section id="about" class="py-24 bg-[#030306] border-t border-white/10 relative overflow-hidden">
      <!-- Section Animated GIF Pattern Background -->
      <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none opacity-25 mix-blend-screen">
        <img src="/pri-sp-vid.gif" alt="Background Pattern" class="w-full h-full object-cover object-center" />
        <div class="absolute inset-0 bg-gradient-to-b from-[#030306] via-transparent to-[#030306]"></div>
      </div>
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Header -->
        <div class="text-center max-w-3xl mx-auto mb-16">
          <span class="text-xs font-mono uppercase tracking-[0.3em] text-purple-400 block mb-3">Our Mission</span>
          <h2 class="text-3xl sm:text-5xl font-chakra-bold font-bold text-white tracking-tight">
            Why KPH Hackathon?
          </h2>
          <p class="mt-4 text-base sm:text-lg leading-relaxed text-neutral-300">
            The mission: Make Kerala the best place to build and launch successful products. We help you go from zero to launch with funding, mentorship, GTM, and your first users. Exciting prizes await!
          </p>
        </div>

        <!-- 3 Feature Cards Grid -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <!-- Card 1 -->
          <div class="bg-[#0b0a17]/90 border border-white/10 hover:border-purple-500/50 rounded-3xl p-7 transition-all duration-300 hover:-translate-y-1.5 hover:shadow-[0_10px_40px_rgba(168,85,247,0.15)] flex flex-col justify-between group backdrop-blur-md">
            <div>
              <div class="w-12 h-12 rounded-2xl bg-purple-950/60 border border-purple-500/30 flex items-center justify-center mb-6 group-hover:scale-110 transition-transform">
                <Rocket class="h-6 w-6 text-purple-300" />
              </div>
              <div class="flex gap-2 mb-3">
                <span class="bg-purple-950/80 border border-purple-800 text-purple-300 text-xs font-mono px-2.5 py-0.5 rounded-full">Mentorship</span>
                <span class="bg-emerald-950/80 border border-emerald-800 text-emerald-300 text-xs font-mono px-2.5 py-0.5 rounded-full">Launch</span>
              </div>
              <h3 class="text-xl font-chakra-bold font-bold text-white mb-2 group-hover:text-purple-300 transition-colors">
                Build & Launch
              </h3>
              <p class="text-sm text-neutral-400 leading-relaxed">
                Go from idea to product launch. Get hands-on support, mentorship, and resources.
              </p>
            </div>
          </div>

          <!-- Card 2 -->
          <div class="bg-[#0b0a17]/90 border border-white/10 hover:border-amber-500/50 rounded-3xl p-7 transition-all duration-300 hover:-translate-y-1.5 hover:shadow-[0_10px_40px_rgba(245,158,11,0.15)] flex flex-col justify-between group backdrop-blur-md">
            <div>
              <div class="w-12 h-12 rounded-2xl bg-amber-950/60 border border-amber-500/30 flex items-center justify-center mb-6 group-hover:scale-110 transition-transform">
                <Wallet class="h-6 w-6 text-amber-300" />
              </div>
              <div class="flex gap-2 mb-3">
                <span class="bg-amber-950/80 border border-amber-800 text-amber-300 text-xs font-mono px-2.5 py-0.5 rounded-full">Funding</span>
                <span class="bg-emerald-950/80 border border-emerald-800 text-emerald-300 text-xs font-mono px-2.5 py-0.5 rounded-full">GTM</span>
              </div>
              <h3 class="text-xl font-chakra-bold font-bold text-white mb-2 group-hover:text-amber-300 transition-colors">
                Funding & GTM
              </h3>
              <p class="text-sm text-neutral-400 leading-relaxed">
                Winners get funding, GTM help, and access to KPH's investor and mentor network.
              </p>
            </div>
          </div>

          <!-- Card 3 -->
          <div class="bg-[#0b0a17]/90 border border-white/10 hover:border-pink-500/50 rounded-3xl p-7 transition-all duration-300 hover:-translate-y-1.5 hover:shadow-[0_10px_40px_rgba(236,72,153,0.15)] flex flex-col justify-between group backdrop-blur-md">
            <div>
              <div class="w-12 h-12 rounded-2xl bg-pink-950/60 border border-pink-500/30 flex items-center justify-center mb-6 group-hover:scale-110 transition-transform">
                <Gift class="h-6 w-6 text-pink-300" />
              </div>
              <div class="flex gap-2 mb-3">
                <span class="bg-pink-950/80 border border-pink-800 text-pink-300 text-xs font-mono px-2.5 py-0.5 rounded-full">Prizes</span>
                <span class="bg-emerald-950/80 border border-emerald-800 text-emerald-300 text-xs font-mono px-2.5 py-0.5 rounded-full">Opportunity</span>
              </div>
              <h3 class="text-xl font-chakra-bold font-bold text-white mb-2 group-hover:text-pink-300 transition-colors">
                Exciting Prizes
              </h3>
              <p class="text-sm text-neutral-400 leading-relaxed">
                Win cash prizes, tools, and exclusive opportunities for your product/startup.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- PREVIOUS HACKATHONS HIGHLIGHTS SECTION -->
    <section id="highlights" class="py-24 bg-[#05040d] border-t border-white/10 relative overflow-hidden">
      <!-- Section Animated GIF Pattern Background -->
      <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none opacity-20 mix-blend-screen">
        <img src="/pri-sp-vid.gif" alt="Background Pattern" class="w-full h-full object-cover object-center" />
        <div class="absolute inset-0 bg-gradient-to-b from-[#05040d] via-transparent to-[#05040d]"></div>
      </div>
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
        <div class="text-center max-w-3xl mx-auto mb-16">
          <span class="text-xs font-mono uppercase tracking-[0.3em] text-pink-400 block mb-3">Relive The Energy</span>
          <h2 class="text-3xl sm:text-5xl font-chakra-bold font-bold text-white tracking-tight">
            Previous Hackathon
          </h2>
          <p class="mt-4 text-base sm:text-lg leading-relaxed text-neutral-300">
            Check out the key moments, project demos, and builder vibes from our past KPH hackathons.
          </p>
        </div>

        <!-- 3 Video Cards Grid -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div
            v-for="video in previousHackathons"
            :key="video.id"
            class="bg-[#0b0a17]/90 border border-white/10 hover:border-purple-500/50 rounded-3xl overflow-hidden group transition-all duration-300 hover:-translate-y-2 shadow-xl backdrop-blur-md flex flex-col justify-between"
          >
            <a :href="video.url" target="_blank" rel="noopener noreferrer" class="block relative aspect-video overflow-hidden">
              <img
                :src="`https://img.youtube.com/vi/${video.videoId}/hqdefault.jpg`"
                :alt="video.title"
                class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-[#030306] via-black/40 to-transparent opacity-70 group-hover:opacity-40 transition-opacity"></div>
              
              <!-- Glowing Play Icon Overlay -->
              <div class="absolute inset-0 flex items-center justify-center">
                <div class="w-14 h-14 rounded-full bg-purple-600/90 text-white flex items-center justify-center shadow-[0_0_25px_rgba(168,85,247,0.8)] group-hover:scale-110 group-hover:bg-pink-600 transition-all duration-300">
                  <Play class="w-6 h-6 fill-current ml-0.5" />
                </div>
              </div>
            </a>
            <div class="p-6">
              <div class="inline-block px-2.5 py-0.5 rounded-full bg-purple-950/80 border border-purple-800 text-purple-300 text-xs font-mono font-medium mb-2">
                Watch Highlights
              </div>
              <h3 class="text-lg font-chakra-bold font-bold text-white group-hover:text-purple-300 transition-colors">
                {{ video.title }}
              </h3>
            </div>
          </div>
        </div>

        <!-- EXPLORE PREVIOUS HACKATHON PRODUCTS CTA LINK -->
        <div class="mt-12 text-center">
          <a
            href="https://launches.kph.club/hackathon"
            target="_blank"
            rel="noopener noreferrer"
            class="group inline-flex items-center gap-3 rounded-full bg-gradient-to-r from-purple-600/90 via-pink-600/90 to-purple-600/90 hover:from-purple-500 hover:to-pink-500 px-8 py-3.5 text-sm sm:text-base font-bold text-white transition-all duration-300 shadow-[0_0_30px_rgba(168,85,247,0.4)] hover:scale-105 border border-purple-400/40 backdrop-blur-xl"
          >
            <Rocket class="h-4 w-4 text-purple-200" />
            <span>Explore Previous Hackathon Products</span>
            <ExternalLink class="h-4 w-4 group-hover:translate-x-1 transition-transform" />
          </a>
        </div>
      </div>
    </section>

    <!-- SPONSOR CTA SECTION (Chakra Petch Bold Title) -->
    <section id="sponsor-info" class="py-24 bg-[#020205] border-t border-white/10 relative overflow-hidden">
      <!-- Section Animated GIF Pattern Background -->
      <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none opacity-25 mix-blend-screen">
        <img src="/pri-sp-vid.gif" alt="Background Pattern" class="w-full h-full object-cover object-center" />
        <div class="absolute inset-0 bg-gradient-to-b from-[#020205] via-transparent to-[#020205]"></div>
      </div>
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Header -->
        <div class="text-center max-w-3xl mx-auto mb-16">
          <span class="text-xs font-mono uppercase tracking-[0.3em] text-cyan-400 block mb-3">Sponsorship</span>
          <h2 class="text-3xl sm:text-5xl font-chakra-bold font-bold text-white tracking-tight">
            Sponsor the KPH Hackathon
          </h2>
          <p class="mt-4 text-base sm:text-lg leading-relaxed text-neutral-300">
            Support Kerala's next wave of founders and product builders. Get your brand in front of the most ambitious makers and innovators in the state. Sponsoring gives you unique access to talent, visibility, and impact.
          </p>
        </div>

        <!-- 2 Sponsor Cards Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 max-w-4xl mx-auto mb-12">
          <article class="bg-[#0a0917]/90 border border-white/10 hover:border-purple-500/50 rounded-3xl p-7 transition-all duration-300 hover:shadow-[0_10px_30px_rgba(168,85,247,0.15)] group backdrop-blur-md">
            <div class="flex items-start gap-4">
              <div class="w-11 h-11 rounded-2xl bg-purple-950/80 border border-purple-500/30 flex items-center justify-center flex-shrink-0 group-hover:scale-110 transition-transform">
                <Users class="h-5 w-5 text-purple-300" />
              </div>
              <div>
                <div class="flex gap-2 mb-2">
                  <span class="bg-blue-950/80 border border-blue-800 text-blue-300 text-xs font-mono px-2.5 py-0.5 rounded-full">Talent</span>
                  <span class="bg-amber-950/80 border border-amber-800 text-amber-300 text-xs font-mono px-2.5 py-0.5 rounded-full">High Impact</span>
                </div>
                <h3 class="text-lg font-chakra-bold font-bold text-white mb-2 group-hover:text-purple-300 transition-colors">
                  Reach Top Talent
                </h3>
                <p class="text-sm text-neutral-400 leading-relaxed">
                  Connect with Kerala's brightest founders, makers, and early-stage startups. Be the first to discover and support emerging talent.
                </p>
              </div>
            </div>
          </article>

          <article class="bg-[#0a0917]/90 border border-white/10 hover:border-purple-500/50 rounded-3xl p-7 transition-all duration-300 hover:shadow-[0_10px_30px_rgba(249,115,22,0.15)] group backdrop-blur-md">
            <div class="flex items-start gap-4">
              <div class="w-11 h-11 rounded-2xl bg-orange-950/80 border border-orange-500/30 flex items-center justify-center flex-shrink-0 group-hover:scale-110 transition-transform">
                <Building2 class="h-5 w-5 text-orange-300" />
              </div>
              <div>
                <div class="flex gap-2 mb-2">
                  <span class="bg-blue-950/80 border border-blue-800 text-blue-300 text-xs font-mono px-2.5 py-0.5 rounded-full">Ecosystem</span>
                  <span class="bg-orange-950/80 border border-orange-800 text-orange-300 text-xs font-mono px-2.5 py-0.5 rounded-full">Impact</span>
                </div>
                <h3 class="text-lg font-chakra-bold font-bold text-white mb-2 group-hover:text-orange-300 transition-colors">
                  Shape the Ecosystem
                </h3>
                <p class="text-sm text-neutral-400 leading-relaxed">
                  Help shape Kerala's product/startup ecosystem and support the next generation of builders. Your sponsorship creates real, lasting impact.
                </p>
              </div>
            </div>
          </article>
        </div>

        <!-- CTA Button -->
        <div class="text-center">
          <button
            @click="sponsorCTA"
            class="group inline-flex items-center gap-3 rounded-full bg-white px-9 py-4 text-base font-bold text-black hover:bg-neutral-200 hover:scale-105 transition-all duration-300 shadow-[0_0_25px_rgba(255,255,255,0.2)]"
          >
            <Rocket class="h-4 w-4" />
            <span>Sponsor the Hackathon</span>
            <ArrowRight class="h-4 w-4 group-hover:translate-x-1.5 transition-transform" />
          </button>
          <p class="mt-4 text-xs font-medium text-neutral-500">
            Partner with us to power Kerala's innovation journey
          </p>
        </div>
      </div>
    </section>

    <!-- FLOATING SPONSOR BUTTON -->
    <button
      @click="sponsorCTA"
      class="fixed z-40 bottom-6 right-6 bg-[#0c0b16]/90 hover:bg-purple-900/90 text-white font-semibold px-5 py-3 rounded-full shadow-[0_8px_30px_rgba(0,0,0,0.8)] flex items-center gap-2 transition-all duration-300 hover:scale-105 text-xs sm:text-sm border border-white/10 backdrop-blur-xl"
    >
      <Rocket class="h-4 w-4 text-purple-400 animate-bounce" />
      <span>Support Hackathon</span>
    </button>

    <!-- FUTURISTIC DARK FOOTER (Styled to match KPH.hack aesthetic) -->
    <footer class="bg-[#030306] border-t border-white/10 text-neutral-300 relative overflow-hidden">
      <!-- Ambient Glow Behind Footer -->
      <div class="absolute inset-0 z-0 overflow-hidden pointer-events-none opacity-20 mix-blend-screen">
        <img src="/pri-sp-vid.gif" alt="Background Pattern" class="w-full h-full object-cover object-center" />
        <div class="absolute inset-0 bg-gradient-to-b from-[#030306] via-transparent to-[#030306]"></div>
      </div>

      <div class="max-w-6xl mx-auto px-6 py-14 lg:px-8 relative z-10">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-10 lg:gap-14">
          <!-- Brand Column -->
          <div class="space-y-4">
            <NuxtLink to="/" class="flex items-center gap-2 group inline-flex">
              <img
                src="/kph-main-logo.png"
                alt="KPH.CLUB"
                class="h-7 w-auto object-contain transition-transform group-hover:scale-105 drop-shadow-[0_0_10px_rgba(255,255,255,0.3)]"
              />
              <span class="font-chakra-bold font-bold text-xl text-white group-hover:text-purple-300 transition-colors">
                KPH<span class="text-purple-400">.</span>hack
              </span>
            </NuxtLink>
            <p class="text-sm text-neutral-400 leading-relaxed max-w-sm">
              Building Kerala's largest product community, one innovation at a time.
            </p>
            <div class="flex items-center space-x-3 pt-2">
              <a
                href="https://www.instagram.com/kph_hackathon/"
                target="_blank"
                rel="noopener noreferrer"
                class="p-2.5 rounded-xl bg-white/5 border border-white/10 hover:border-purple-500/50 hover:bg-purple-950/40 text-neutral-300 hover:text-purple-300 transition-all duration-300 hover:scale-110 shadow-sm"
              >
                <Instagram class="h-4 w-4" />
              </a>
              <a
                href="https://x.com/keralaph"
                target="_blank"
                rel="noopener noreferrer"
                class="p-2.5 rounded-xl bg-white/5 border border-white/10 hover:border-purple-500/50 hover:bg-purple-950/40 text-neutral-300 hover:text-purple-300 transition-all duration-300 hover:scale-110 shadow-sm"
              >
                <Twitter class="h-4 w-4" />
              </a>
              <a
                href="https://www.youtube.com/@FelixJosemonOfficial/videos"
                target="_blank"
                rel="noopener noreferrer"
                class="p-2.5 rounded-xl bg-white/5 border border-white/10 hover:border-purple-500/50 hover:bg-purple-950/40 text-neutral-300 hover:text-purple-300 transition-all duration-300 hover:scale-110 shadow-sm"
              >
                <Youtube class="h-4 w-4" />
              </a>
              <a
                href="https://in.linkedin.com/company/keralaph"
                target="_blank"
                rel="noopener noreferrer"
                class="p-2.5 rounded-xl bg-white/5 border border-white/10 hover:border-purple-500/50 hover:bg-purple-950/40 text-neutral-300 hover:text-purple-300 transition-all duration-300 hover:scale-110 shadow-sm"
              >
                <Linkedin class="h-4 w-4" />
              </a>
            </div>
          </div>

          <!-- Quick Links -->
          <div>
            <h3 class="text-white font-chakra-bold text-sm font-semibold mb-5 tracking-wider uppercase">Quick Links</h3>
            <ul class="space-y-3 text-sm">
              <li>
                <NuxtLink to="https://nas.io/kphjobs" target="_blank" rel="noopener noreferrer" class="text-neutral-400 hover:text-purple-300 transition-colors inline-block">
                  Jobs
                </NuxtLink>
              </li>
              <li>
                <NuxtLink to="https://wiki.kph.club" target="_blank" rel="noopener noreferrer" class="text-neutral-400 hover:text-purple-300 transition-colors inline-block">
                  Wiki
                </NuxtLink>
              </li>
              <li>
                <NuxtLink to="https://blog.kph.club" target="_blank" rel="noopener noreferrer" class="text-neutral-400 hover:text-purple-300 transition-colors inline-block">
                  Blog
                </NuxtLink>
              </li>
            </ul>
          </div>

          <!-- Resources -->
          <div>
            <h3 class="text-white font-chakra-bold text-sm font-semibold mb-5 tracking-wider uppercase">Resources</h3>
            <ul class="space-y-3 text-sm">
              <li>
                <a href="https://wiki.kph.club" target="_blank" rel="noopener noreferrer" class="text-neutral-400 hover:text-purple-300 transition-colors inline-block">
                  Startup Wiki
                </a>
              </li>
              <li>
                <a href="https://www.youtube.com/@FelixJosemonOfficial/videos" target="_blank" rel="noopener noreferrer" class="text-neutral-400 hover:text-purple-300 transition-colors inline-block">
                  Podcasts
                </a>
              </li>
              <li>
                <a href="https://learn.kph.club" target="_blank" rel="noopener noreferrer" class="text-neutral-400 hover:text-purple-300 transition-colors inline-block">
                  Masterclass
                </a>
              </li>
            </ul>
          </div>
        </div>

        <!-- Bottom Bar -->
        <div class="mt-12 pt-8 border-t border-white/10 flex flex-col md:flex-row justify-between items-center gap-4 text-xs sm:text-sm text-neutral-400 font-mono">
          <p>
            © {{ new Date().getFullYear() }} KPH. All rights reserved.
          </p>
          <p>
            built by <a href="https://austin-portfolio-phi.vercel.app/" target="_blank" rel="noopener noreferrer" class="text-purple-300 hover:text-purple-200 underline font-semibold transition-colors">Austin</a>
          </p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { Rocket, Wallet, Gift, ArrowRight, Users, Building2, Play, Trophy, Sparkles, Code2, Cpu, Instagram, Twitter, Youtube, Linkedin, ExternalLink, Clock, Flame, Quote } from 'lucide-vue-next'

// Page Loading Preloader State
const isLoading = ref(true)
const progress = ref(0)

// Preloader Builder Quotes
const quotes = [
  { text: "The best way to predict the future is to invent it.", author: "Alan Kay" },
  { text: "Great products aren't built in quiet moments. They are forged in intense focus.", author: "KPH Hackathon '26" },
  { text: "Ideas are cheap. Execution is everything.", author: "John Doerr" },
  { text: "Make something people want, then build fast.", author: "Paul Graham" },
  { text: "Kerala's biggest product revolution begins October 3, 2026.", author: "KPH Community" }
]
const currentQuoteIndex = ref(0)
const currentQuote = computed(() => quotes[currentQuoteIndex.value])

// Hero Countdown Timer towards OCTOBER 3 2026
const targetDate = new Date('2026-10-03T00:00:00')
const timeLeft = ref({
  days: '00',
  hours: '00',
  minutes: '00',
  seconds: '00'
})

let countdownTimer = null
let quoteTimer = null

const calculateTimeLeft = () => {
  const now = new Date().getTime()
  const difference = targetDate.getTime() - now

  if (difference <= 0) {
    timeLeft.value = { days: '00', hours: '00', minutes: '00', seconds: '00' }
    if (countdownTimer) clearInterval(countdownTimer)
    return
  }

  const d = Math.floor(difference / (1000 * 60 * 60 * 24))
  const h = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
  const m = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60))
  const s = Math.floor((difference % (1000 * 60)) / 1000)

  timeLeft.value = {
    days: String(d).padStart(2, '0'),
    hours: String(h).padStart(2, '0'),
    minutes: String(m).padStart(2, '0'),
    seconds: String(s).padStart(2, '0')
  }
}

// Mouse movement interactive spotlight
const mouseX = ref(0)
const mouseY = ref(0)

const handleMouseMove = (event) => {
  const rect = event.currentTarget.getBoundingClientRect()
  mouseX.value = (event.clientX - rect.left - rect.width / 2) * 0.04
  mouseY.value = (event.clientY - rect.top - rect.height / 2) * 0.04
}

// Active Track Pill hover state
const activeTrack = ref(null)
const tracks = [
  { id: 'ai', name: 'AI & Agents', icon: Sparkles, color: 'text-purple-400', bg: 'bg-purple-950/60 border-purple-500/40' },
  { id: 'saas', name: 'SaaS & DevTools', icon: Code2, color: 'text-cyan-400', bg: 'bg-cyan-950/60 border-cyan-500/40' },
  { id: 'hardware', name: 'Hardware & IoT', icon: Cpu, color: 'text-pink-400', bg: 'bg-pink-950/60 border-pink-500/40' }
]

onMounted(() => {
  // Initialize countdown calculation
  calculateTimeLeft()
  countdownTimer = setInterval(calculateTimeLeft, 1000)

  // Rotate quotes during preloader
  quoteTimer = setInterval(() => {
    currentQuoteIndex.value = (currentQuoteIndex.value + 1) % quotes.length
  }, 2000)

  // Preloader progress simulation
  const progressInterval = setInterval(() => {
    if (progress.value < 100) {
      progress.value += Math.floor(Math.random() * 25) + 18
      if (progress.value > 100) progress.value = 100
    } else {
      clearInterval(progressInterval)
      if (quoteTimer) clearInterval(quoteTimer)
      setTimeout(() => {
        isLoading.value = false
      }, 350)
    }
  }, 120)
})

onUnmounted(() => {
  if (countdownTimer) clearInterval(countdownTimer)
  if (quoteTimer) clearInterval(quoteTimer)
})

// Previous Hackathons video links
const previousHackathons = [
  {
    id: 1,
    videoId: 'yo2HQgfLChU',
    title: 'KPH Hackathon Highlights',
    url: 'https://youtu.be/yo2HQgfLChU?si=ml-MRHRS7J9VTvuC'
  },
  {
    id: 2,
    videoId: 'BtiujRwSTag',
    title: 'KPH Hackathon Demo Day & Aftermovie',
    url: 'https://youtu.be/BtiujRwSTag?si=qOtTSaEyGQJ-46OZ'
  },
  {
    id: 3,
    videoId: 'ie8dKsWa0pg',
    title: 'KPH Hackathon Stories & Projects',
    url: 'https://youtu.be/ie8dKsWa0pg?si=D9sWOo_vONOurhgG'
  }
]

// Meta tags and head configuration
useHead({
  htmlAttrs: {
    lang: 'en'
  },
  title: 'KPH Hackathon - Build and Launch | October 3, 2026',
  meta: [
    { name: 'description', content: 'Join the KPH Hackathon on October 3, 2026. Build and launch your product with funding, mentorship, GTM support, and exciting prizes.' },
    { property: 'og:title', content: 'KPH Hackathon - Build and Launch | October 3, 2026' },
    { property: 'og:description', content: 'Join the KPH Hackathon on October 3, 2026. Build and launch your product with funding, mentorship, GTM support, and exciting prizes.' },
    { property: 'og:url', content: 'https://kph.club/archives/hack' },
    { property: 'og:image', content: '/accelerator-og.png' },
    { property: 'og:type', content: 'website' }
  ],
  link: [
    { rel: 'icon', type: 'image/png', href: '/favicon.png' },
    { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
    { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: '' },
    { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css2?family=Chakra+Petch:wght@700&display=swap' }
  ]
})

// Sponsor CTA function
const sponsorCTA = () => {
  window.open('https://api.whatsapp.com/send/?phone=917025437098&text=Hi%2C+I%27d+love+to+sponsor+and+support+the+hackathon', '_blank')
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Chakra+Petch:wght@700&display=swap');

.font-chakra-bold {
  font-family: 'Chakra Petch', sans-serif;
  font-weight: 700;
}

/* Halftone Float Animations */
@keyframes floatLeft {
  0%, 100% { transform: translateY(-50%) translateX(0px); }
  50% { transform: translateY(-50%) translateX(-8px); }
}

@keyframes floatRight {
  0%, 100% { transform: translateY(-50%) translateX(0px); }
  50% { transform: translateY(-50%) translateX(8px); }
}

@keyframes floatCenter {
  0%, 100% { transform: translateY(0px) scale(1); }
  50% { transform: translateY(-10px) scale(1.02); }
}

@keyframes spinSlow {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.animate-float-left {
  animation: floatLeft 5s ease-in-out infinite;
}

.animate-float-right {
  animation: floatRight 5s ease-in-out infinite;
}

.animate-float-center {
  animation: floatCenter 6s ease-in-out infinite;
}

.animate-spin-slow {
  animation: spinSlow 22s linear infinite;
}

/* Hero Title & Subtitle Entrance and Glow Animations */
@keyframes heroTextIn {
  from {
    opacity: 0;
    transform: translateY(28px) scale(0.95);
    filter: blur(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
    filter: blur(0);
  }
}

@keyframes titleGlowPulse {
  0%, 100% {
    text-shadow: 0 0 25px rgba(168, 85, 247, 0.4), 0 0 50px rgba(168, 85, 247, 0.2);
  }
  50% {
    text-shadow: 0 0 40px rgba(236, 72, 153, 0.6), 0 0 70px rgba(6, 182, 212, 0.3);
  }
}

@keyframes subtitleGradientFlow {
  0%, 100% {
    background-position: 0% 50%;
    filter: drop-shadow(0 0 15px rgba(168, 85, 247, 0.4));
  }
  50% {
    background-position: 100% 50%;
    filter: drop-shadow(0 0 30px rgba(236, 72, 153, 0.6));
  }
}

.animate-title-glow {
  animation: heroTextIn 1.1s cubic-bezier(0.16, 1, 0.3, 1) forwards, titleGlowPulse 5s ease-in-out infinite 1.1s;
}

.animate-subtitle-glow {
  background-size: 200% 200%;
  animation: heroTextIn 1.1s cubic-bezier(0.16, 1, 0.3, 1) 0.2s forwards, subtitleGradientFlow 6s ease-in-out infinite 1.3s;
}

/* Marquee Animation */
@keyframes marquee {
  0% { transform: translateX(0%); }
  100% { transform: translateX(-50%); }
}

.animate-marquee {
  display: flex;
  width: max-content;
  animation: marquee 25s linear infinite;
}

.animate-marquee:hover {
  animation-play-state: paused;
}

@keyframes spinReverse {
  from { transform: rotate(360deg); }
  to { transform: rotate(0deg); }
}

.animate-spin-reverse {
  animation: spinReverse 1.5s linear infinite;
}

/* Preloader Quote Fade Animation */
@keyframes quoteFadeIn {
  0% {
    opacity: 0;
    transform: translateY(8px);
    filter: blur(4px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
    filter: blur(0);
  }
}

.animate-quote-fade {
  animation: quoteFadeIn 0.5s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}
</style>