
<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}

const navigation = [
  { name: 'Home', number: '01', href: '#home' },
  { name: 'About', number: '02', href: '#about' },
  { name: 'Works', number: '03', href: '#works' },
  { name: 'Contact', number: '04', href: '#contact' },
]
</script>

<template>
  <main
    class="relative isolate min-h-screen overflow-hidden bg-[#101112] text-white
    [background:radial-gradient(ellipse_at_50%_100%,rgba(10,55,62,0.48),transparent_50%),linear-gradient(180deg,#171515_0%,#101112_48%,#0b171a_100%)]"
  >
    <!-- Navbar -->
    <header
      class="relative z-20 flex items-center justify-between px-[3.4%] py-10 md:py-12"
    >
      <a
        href="#home"
        class="text-[20px] font=['Orbitron'] font-medium tracking-wide transition-opacity hover:opacity-60 md:text-[27px]"
      >
        ARTPHORIA
      </a>

      <!-- Menu Button -->
      <button
        @click="toggleMenu"
        :class="{ 'active': menuOpen }"
        class="menu-trigger grid grid-cols-3 gap-[4px] p-2"
        aria-label="Toggle navigation"
        :aria-expanded="menuOpen"
      >
        <span v-for="n in 9" :key="n"></span>
      </button>
    </header>

    <!-- Navigation Overlay -->
    <Transition name="menu">
      <nav
        v-if="menuOpen"
        class="fixed inset-0 z-30 flex flex-col justify-center bg-[#0a0c0d]/30 px-[8%] py-20 backdrop-blur-2xl md:px-[13%]"
      >
        <button
          @click="toggleMenu"
          class="absolute right-[6%] top-10 flex items-center gap-3 text-[11px] tracking-[2px] transition-colors hover:text-[#a5f3e9]"
        >
          CLOSE <span class="text-2xl">×</span>
        </button>

        <a
          v-for="item in navigation"
          :key="item.number"
          :href="item.href"
          @click="toggleMenu"
          class="flex items-center justify-between border-b border-white/15 py-4 text-3xl transition-colors hover:text-[#a5f3e9] md:text-6xl"
        >
          {{ item.name }}
          <span class="font-sans text-xs text-white/40">
            {{ item.number }}
          </span>
        </a>

        <p class="mt-10 text-[9px] tracking-[3px] text-white/40">
          ARTPHORIA — CREATIVE IN MONOLITH
        </p>
      </nav>
    </Transition>

    <!-- Hero Section -->
    <section
      id="home"
      class="relative z-[2] flex min-h-[calc(100svh-110px)] items-center justify-center px-6 pb-36 md:pb-28"
    >
      <div
        class="hero-enter flex w-full max-w-[900px] flex-col items-center justify-center gap-7 text-center md:flex-row md:gap-[52px] md:text-left"
      >
        <!-- Logo -->

        <div class="relative flex w-[120px] shrink-0 items-center justify-center md:w-[350px]">

          <!-- Vertical Spotlight -->
          <div class="logo-spotlight"></div>

          <!-- Logo -->
          <img
            src="/logo.png"
            alt="Arthiphoria Logo"
            class="logo-glow relative z-[2] h-auto w-full object-contain"
          />

        </div>


        <!-- Content -->
        <div class="min-w-0">
          <span
            class="mb-3 block text-[8px] font-medium tracking-[3px] text-white/50 md:text-[9px] md:tracking-[4px]"
          >
            CREATIVE COLLECTIVE / EST. 2026
          </span>

          <h1
            class="whitespace-nowrap text-[30px] font-medium tracking-[-2px] md:text-[clamp(35px,4vw,58px)]"
          >
            ARTIPHORIA<span class="text-[#a5f3e9]">.</span>
          </h1>

          <p
            class="mt-5 text-[16px] font-light leading-[1.55] tracking-[-0.8px] sm:text-xl md:text-[clamp(18px,2.5vw,28px)]"
          >
            In one monolith<br />
            creating euphoria from elegant art.
          </p>

          <div
            class="hero-line mx-auto mt-7 h-[1px] w-[110px] origin-left bg-white md:mx-0 md:mt-11 md:w-[175px]"
          ></div>
        </div>
      </div>
    </section>

    <!-- Orbital Rings -->
    <div
      class="orbital-system pointer-events-none absolute bottom-[75px] left-1/2 z-[1] h-[120px] w-[115vw] -translate-x-1/2 md:bottom-[65px] md:h-[190px] md:w-[78vw]"
      aria-hidden="true"
    >
      <div class="orbit orbit-one"></div>
      <div class="orbit orbit-two"></div>
      <div class="orbit orbit-three"></div>
    </div>

    <!-- Footer -->
    <footer
      class="absolute bottom-[25px] left-0 z-[3] flex w-full items-center justify-between px-[6%] text-[6px] tracking-[1px] text-white/40 md:px-[3.4%] md:text-[8px] md:tracking-[2px]"
    >
      <span>IN ONE MONOLITH</span>

      <span class="hidden md:block">
        CREATING EUPHORIA FROM ELEGANT ART.
      </span>

      <span>SCROLL TO EXPLORE ↓</span>
    </footer>
  </main>
</template>
