<template>
  <section id="tentang" class="py-24 px-6">
    <div class="max-w-6xl mx-auto">
      <!-- Section header -->
      <div class="mb-16">
        <p class="font-mono text-[#00f5ff] text-sm mb-2">// 01. about</p>
        <h2 class="text-4xl font-black text-[#e2f0ff]">Tentang <span class="gradient-text">Saya</span></h2>
        <div class="mt-3 w-16 h-0.5 bg-gradient-to-r from-[#00f5ff] to-transparent"></div>
      </div>

      <div class="grid lg:grid-cols-5 gap-12 items-start">
        <!-- Avatar / visual side -->
        <div class="lg:col-span-2 flex justify-center lg:justify-start">
          <div class="relative">
            <!-- Avatar container -->
            <div class="w-56 h-56 rounded-xl neon-card flex items-center justify-center text-8xl relative overflow-hidden">
              <div class="absolute inset-0 bg-gradient-to-br from-[#00f5ff]/10 to-[#00ff88]/5"></div>
              <span class="relative z-10">👨‍💻</span>
            </div>
            <!-- Decorative corner lines -->
            <div class="absolute -top-2 -left-2 w-8 h-8 border-t-2 border-l-2 border-[#00f5ff]"></div>
            <div class="absolute -bottom-2 -right-2 w-8 h-8 border-b-2 border-r-2 border-[#00f5ff]"></div>

            <!-- Stat cards -->
            <div class="absolute -right-8 top-4 neon-card rounded-lg px-4 py-3 text-center min-w-[90px]">
              <p class="text-2xl font-black text-[#00f5ff]">5+</p>
              <p class="font-mono text-[10px] text-[#6b8cad]">Proyek</p>
            </div>
            <div class="absolute -left-8 bottom-4 neon-card rounded-lg px-4 py-3 text-center min-w-[90px]">
              <p class="text-2xl font-black text-[#00ff88]">3+</p>
              <p class="font-mono text-[10px] text-[#6b8cad]">Teknologi</p>
            </div>
          </div>
        </div>

        <!-- Text side -->
        <div class="lg:col-span-3 space-y-6">
          <div class="space-y-4 text-[#8fafc7] leading-relaxed">
            <p>
              Saya adalah mahasiswa Informatika tingkat akhir di
              <span class="text-[#00f5ff] font-medium">Universitas Muhammadiyah Malang</span>,
              dengan minat utama di bidang <span class="text-[#e2f0ff] font-medium">Rekayasa Perangkat Lunak</span>.
              Saya tertarik pada pengembangan aplikasi web dan mobile, terutama di sisi backend.
            </p>
            <p>
              Saya menikmati proses membangun sistem dari
              <span class="text-[#00ff88]">desain API</span>,
              <span class="text-[#00ff88]">struktur database</span>,
              <span class="text-[#00ff88]">integrasi frontend-backend</span>,
              hingga <span class="text-[#00ff88]">alur deployment sederhana</span>.
              Bagi saya, kode yang baik bukan hanya yang berfungsi, tapi yang mudah dipahami dan dipelihara.
            </p>
            <p>
              Di luar coding, saya aktif mengeksplorasi konsep software engineering,
              arsitektur sistem, dan pola desain yang dapat diterapkan pada proyek nyata.
            </p>
          </div>

          <!-- Info grid -->
          <div class="grid grid-cols-2 gap-4 pt-4">
            <div v-for="info in infos" :key="info.label"
              class="flex items-start gap-3 p-4 rounded-lg bg-[#0a1628] border border-[rgba(0,245,255,0.08)]">
              <span class="text-xl">{{ info.icon }}</span>
              <div>
                <p class="font-mono text-[10px] text-[#6b8cad] uppercase tracking-widest">{{ info.label }}</p>
                <p class="text-sm text-[#e2f0ff] mt-0.5">{{ info.value }}</p>
              </div>
            </div>
          </div>

          <!-- Download CV -->
          <div class="pt-2">
            <a href="#" class="inline-flex items-center gap-2 font-mono text-sm text-[#6b8cad] hover:text-[#00f5ff] transition-colors duration-200 border-b border-dashed border-[#6b8cad]/30 hover:border-[#00f5ff]/50 pb-0.5">
              <span>↓</span> Unduh CV
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AboutSection',
  data() {
    return {
      infos: [
        { icon: '🎓', label: 'Universitas', value: 'Univ. Muhammadiyah Malang' },
        { icon: '📚', label: 'Jurusan', value: 'Teknik Informatika' },
        { icon: '🎯', label: 'Minat', value: 'Software Engineering' },
        { icon: '📍', label: 'Lokasi', value: 'Malang, Jawa Timur' },
      ],
    }
  },
}
</script>
