<template>
  <section id="hero" class="relative min-h-screen flex items-center justify-center px-6 pt-16">
    <div class="max-w-6xl mx-auto w-full grid lg:grid-cols-2 gap-12 items-center">

      <!-- Left: Text content -->
      <div class="space-y-6">
        <!-- Status badge -->
        <div class="inline-flex items-center gap-2 px-3 py-1.5 border border-[#00ff88]/30 rounded-full bg-[#00ff88]/5">
          <span class="w-2 h-2 rounded-full bg-[#00ff88] animate-pulse"></span>
          <span class="font-mono text-xs text-[#00ff88]">Tersedia untuk kolaborasi</span>
        </div>

        <!-- Name -->
        <div>
          <p class="font-mono text-[#6b8cad] text-sm mb-2">// Halo, saya</p>
          <h1 class="font-display text-5xl lg:text-6xl font-black leading-tight">
            <span class="text-[#e2f0ff]">Hasbi Ash</span><br />
            <span class="gradient-text">Shiddiqi</span>
          </h1>
        </div>

        <!-- Role -->
        <div class="font-mono text-lg text-[#6b8cad]">
          <span class="text-[#00f5ff]">const</span>
          <span class="text-[#e2f0ff]"> role</span>
          <span class="text-[#6b8cad]"> = </span>
          <span class="text-[#00ff88]">"</span>
          <span class="text-[#e2f0ff]">{{ displayedRole }}</span>
          <span v-if="typing" class="text-[#00f5ff] animate-[blink_1s_infinite]">|</span>
          <span class="text-[#00ff88]">"</span>
        </div>

        <!-- Description -->
        <p class="text-[#8fafc7] leading-relaxed max-w-lg text-base">
          Mahasiswa Informatika tingkat akhir di
          <span class="text-[#00f5ff]">Universitas Muhammadiyah Malang</span>,
          fokus pada pengembangan backend dan sistem berbasis API.
          Suka membangun hal-hal yang benar-benar berfungsi.
        </p>

        <!-- CTA buttons -->
        <div class="flex flex-wrap gap-4 pt-2">
          <a
            href="#proyek"
            class="group flex items-center gap-2 px-6 py-3 bg-[#00f5ff] text-[#050a0f] font-bold rounded font-mono text-sm hover:bg-[#00d4e0] transition-all duration-200 glow-cyan"
          >
            Lihat Proyek
            <span class="group-hover:translate-x-1 transition-transform duration-200">→</span>
          </a>
          <a
            href="#kontak"
            class="flex items-center gap-2 px-6 py-3 border border-[#00f5ff]/30 text-[#00f5ff] font-mono text-sm rounded hover:bg-[#00f5ff]/10 hover:border-[#00f5ff]/60 transition-all duration-200"
          >
            Hubungi Saya
          </a>
        </div>

        <!-- Social links -->
        <div class="flex items-center gap-6 pt-2">
          <a href="https://github.com/hsdiqi" target="_blank" rel="noopener"
            class="text-[#6b8cad] hover:text-[#00f5ff] transition-colors duration-200 font-mono text-xs flex items-center gap-1.5">
            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"/>
            </svg>
            GitHub
          </a>
          <a href="https://linkedin.com/in/hsdiqi" target="_blank" rel="noopener"
            class="text-[#6b8cad] hover:text-[#00f5ff] transition-colors duration-200 font-mono text-xs flex items-center gap-1.5">
            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
            LinkedIn
          </a>
        </div>
      </div>

      <!-- Right: Terminal card -->
      <div class="relative">
        <!-- Glow backdrop -->
        <div class="absolute inset-0 bg-[#00f5ff]/5 rounded-xl blur-xl"></div>

        <div class="relative neon-card rounded-xl overflow-hidden scanline">
          <!-- Terminal header -->
          <div class="flex items-center gap-2 px-4 py-3 bg-[#0a1628] border-b border-[rgba(0,245,255,0.1)]">
            <span class="w-3 h-3 rounded-full bg-[#ff5f57]"></span>
            <span class="w-3 h-3 rounded-full bg-[#febc2e]"></span>
            <span class="w-3 h-3 rounded-full bg-[#28c840]"></span>
            <span class="ml-4 font-mono text-xs text-[#6b8cad]">~/hsdiqi/whoami.sh</span>
          </div>

          <!-- Terminal body -->
          <div class="p-6 font-mono text-sm space-y-3">
            <div class="flex gap-2">
              <span class="text-[#00ff88]">hsdiqi@dev</span>
              <span class="text-[#6b8cad]">~$</span>
              <span class="text-[#e2f0ff]">whoami</span>
            </div>

            <div class="pl-4 space-y-2 text-[#8fafc7]">
              <p><span class="text-[#00f5ff]">name:</span> <span class="text-[#e2f0ff]">Hasbi Ash Shiddiqi</span></p>
              <p><span class="text-[#00f5ff]">alias:</span> <span class="text-[#00ff88]">hsdiqi</span></p>
              <p><span class="text-[#00f5ff]">role:</span> <span class="text-[#e2f0ff]">Backend Dev & Mobile Dev</span></p>
              <p><span class="text-[#00f5ff]">university:</span> <span class="text-[#e2f0ff]">UMM</span></p>
              <p><span class="text-[#00f5ff]">major:</span> <span class="text-[#e2f0ff]">Informatika</span></p>
              <p><span class="text-[#00f5ff]">focus:</span> <span class="text-[#bf5fff]">Software Engineering</span></p>
            </div>

            <div class="flex gap-2 mt-2">
              <span class="text-[#00ff88]">hsdiqi@dev</span>
              <span class="text-[#6b8cad]">~$</span>
              <span class="text-[#e2f0ff]">ls skills/</span>
            </div>

            <div class="pl-4 flex flex-wrap gap-2">
              <span v-for="skill in quickSkills" :key="skill"
                class="px-2 py-0.5 text-xs rounded border border-[rgba(0,245,255,0.2)] text-[#00f5ff]">
                {{ skill }}
              </span>
            </div>

            <div class="flex gap-2 mt-2">
              <span class="text-[#00ff88]">hsdiqi@dev</span>
              <span class="text-[#6b8cad]">~$</span>
              <span class="cursor-blink text-[#e2f0ff]"> </span>
            </div>
          </div>
        </div>

        <!-- Floating badges -->
        <div class="absolute -top-4 -right-4 px-3 py-1.5 bg-[#0d1f35] border border-[#00ff88]/40 rounded-full font-mono text-xs text-[#00ff88] glow-green">
          ✓ Open to Work
        </div>
        <div class="absolute -bottom-4 -left-4 px-3 py-1.5 bg-[#0d1f35] border border-[#bf5fff]/40 rounded-full font-mono text-xs text-[#bf5fff]">
          🎓 Final Year
        </div>
      </div>
    </div>

    <!-- Scroll indicator -->
    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2">
      <span class="font-mono text-xs text-[#6b8cad]">scroll</span>
      <div class="w-px h-12 bg-gradient-to-b from-[#00f5ff] to-transparent animate-bounce"></div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  data() {
    return {
      roles: [
        'Backend Developer',
        'Mobile Developer',
        'Fullstack Learner',
        'API Engineer',
      ],
      roleIndex: 0,
      displayedRole: '',
      typing: true,
      charIndex: 0,
      quickSkills: ['Golang', 'Vue', 'Flutter', 'Docker', 'MySQL', 'Git'],
    }
  },
  mounted() {
    this.typeRole()
  },
  methods: {
    typeRole() {
      const current = this.roles[this.roleIndex]
      if (this.charIndex < current.length) {
        this.displayedRole += current[this.charIndex]
        this.charIndex++
        setTimeout(this.typeRole, 80)
      } else {
        this.typing = false
        setTimeout(this.eraseRole, 2000)
      }
    },
    eraseRole() {
      if (this.displayedRole.length > 0) {
        this.displayedRole = this.displayedRole.slice(0, -1)
        setTimeout(this.eraseRole, 40)
      } else {
        this.roleIndex = (this.roleIndex + 1) % this.roles.length
        this.charIndex = 0
        this.typing = true
        setTimeout(this.typeRole, 300)
      }
    },
  },
}
</script>
