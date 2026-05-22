<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      scrolled
        ? 'bg-[#050a0f]/90 backdrop-blur-md border-b border-[rgba(0,245,255,0.1)]'
        : 'bg-transparent'
    ]"
  >
    <div class="max-w-6xl mx-auto px-6 h-16 flex items-center justify-between">
      <!-- Logo -->
      <a href="#hero" class="flex items-center gap-2 group">
        <span class="font-mono text-[#00f5ff] text-xl font-bold tracking-wider group-hover:text-glow-cyan transition-all duration-300">
          &lt;hsdiqi /&gt;
        </span>
      </a>

      <!-- Desktop nav -->
      <div class="hidden md:flex items-center gap-8">
        <a
          v-for="item in navItems"
          :key="item.href"
          :href="item.href"
          class="font-mono text-sm text-[#6b8cad] hover:text-[#00f5ff] transition-colors duration-200 relative group"
        >
          <span class="text-[#00f5ff] opacity-60 mr-1">./</span>{{ item.label }}
          <span class="absolute -bottom-1 left-0 w-0 h-px bg-[#00f5ff] group-hover:w-full transition-all duration-300"></span>
        </a>
      </div>

      <!-- CTA -->
      <a
        href="#kontak"
        class="hidden md:flex items-center gap-2 px-4 py-2 border border-[#00f5ff]/40 text-[#00f5ff] font-mono text-sm rounded hover:bg-[#00f5ff]/10 hover:border-[#00f5ff]/80 transition-all duration-200"
      >
        <span class="w-2 h-2 rounded-full bg-[#00ff88] animate-pulse"></span>
        Hubungi
      </a>

      <!-- Mobile hamburger -->
      <button
        @click="mobileOpen = !mobileOpen"
        class="md:hidden flex flex-col gap-1.5 p-2"
        aria-label="Toggle menu"
      >
        <span :class="['block w-6 h-0.5 bg-[#00f5ff] transition-all duration-300', mobileOpen ? 'rotate-45 translate-y-2' : '']"></span>
        <span :class="['block w-6 h-0.5 bg-[#00f5ff] transition-all duration-300', mobileOpen ? 'opacity-0' : '']"></span>
        <span :class="['block w-6 h-0.5 bg-[#00f5ff] transition-all duration-300', mobileOpen ? '-rotate-45 -translate-y-2' : '']"></span>
      </button>
    </div>

    <!-- Mobile menu -->
    <transition name="slide-down">
      <div
        v-if="mobileOpen"
        class="md:hidden bg-[#050a0f]/95 backdrop-blur-md border-b border-[rgba(0,245,255,0.1)] px-6 py-4 flex flex-col gap-4"
      >
        <a
          v-for="item in navItems"
          :key="item.href"
          :href="item.href"
          @click="mobileOpen = false"
          class="font-mono text-sm text-[#6b8cad] hover:text-[#00f5ff] transition-colors duration-200"
        >
          <span class="text-[#00f5ff] opacity-60 mr-1">./</span>{{ item.label }}
        </a>
      </div>
    </transition>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      scrolled: false,
      mobileOpen: false,
      navItems: [
        { href: '#tentang', label: 'Tentang' },
        { href: '#keahlian', label: 'Keahlian' },
        { href: '#proyek', label: 'Proyek' },
        { href: '#pengalaman', label: 'Pengalaman' },
        { href: '#kontak', label: 'Kontak' },
      ],
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.scrolled = window.scrollY > 20
    },
  },
}
</script>

<style scoped>
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease;
}
.slide-down-enter-from,
.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
