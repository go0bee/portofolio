<template>
  <section id="pengalaman" class="py-24 px-6 bg-[#050e1a]">
    <div class="max-w-6xl mx-auto">
      <!-- Header -->
      <div class="mb-16">
        <p class="font-mono text-[#00f5ff] text-sm mb-2">// 04. experience</p>
        <h2 class="text-4xl font-black text-[#e2f0ff]">Pengalaman <span class="gradient-text">&amp; Pendidikan</span></h2>
        <div class="mt-3 w-16 h-0.5 bg-gradient-to-r from-[#00f5ff] to-transparent"></div>
      </div>

      <div class="grid lg:grid-cols-2 gap-16">
        <!-- Experience timeline -->
        <div>
          <h3 class="font-mono text-sm text-[#00ff88] mb-8 flex items-center gap-2">
            <span class="w-4 h-px bg-[#00ff88]"></span>
            Pengalaman Kerja
          </h3>
          <div class="relative">
            <!-- Timeline line -->
            <div class="absolute left-3 top-0 bottom-0 w-px bg-gradient-to-b from-[#00f5ff]/40 via-[#00f5ff]/20 to-transparent"></div>

            <div class="space-y-8">
              <div
                v-for="(exp, idx) in experiences"
                :key="idx"
                class="relative pl-10 group"
              >
                <!-- Dot -->
                <div class="absolute left-0 top-1 w-6 h-6 rounded-full border-2 border-[#00f5ff] bg-[#050a0f] flex items-center justify-center group-hover:bg-[#00f5ff]/20 transition-colors duration-300">
                  <div class="w-2 h-2 rounded-full bg-[#00f5ff]"></div>
                </div>

                <!-- Card -->
                <div class="neon-card rounded-xl p-5 hover:border-[#00f5ff]/40">
                  <div class="flex flex-wrap items-start justify-between gap-2 mb-2">
                    <h4 class="font-bold text-[#e2f0ff]">{{ exp.role }}</h4>
                    <span class="font-mono text-[10px] px-2 py-0.5 rounded bg-[#00f5ff]/10 text-[#00f5ff]">
                      {{ exp.period }}
                    </span>
                  </div>
                  <p class="font-mono text-sm text-[#00ff88] mb-2">{{ exp.company }}</p>
                  <p class="text-sm text-[#6b8cad] leading-relaxed mb-3">{{ exp.description }}</p>
                  <div class="flex flex-wrap gap-2">
                    <span
                      v-for="tag in exp.tags"
                      :key="tag"
                      class="px-2 py-0.5 text-[10px] font-mono rounded border border-[rgba(0,245,255,0.15)] text-[#8fafc7]"
                    >{{ tag }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Education timeline -->
        <div>
          <h3 class="font-mono text-sm text-[#bf5fff] mb-8 flex items-center gap-2">
            <span class="w-4 h-px bg-[#bf5fff]"></span>
            Pendidikan
          </h3>
          <div class="relative">
            <div class="absolute left-3 top-0 bottom-0 w-px bg-gradient-to-b from-[#bf5fff]/40 via-[#bf5fff]/20 to-transparent"></div>

            <div class="space-y-8">
              <div
                v-for="(edu, idx) in educations"
                :key="idx"
                class="relative pl-10 group"
              >
                <div class="absolute left-0 top-1 w-6 h-6 rounded-full border-2 border-[#bf5fff] bg-[#050a0f] flex items-center justify-center group-hover:bg-[#bf5fff]/20 transition-colors duration-300">
                  <div class="w-2 h-2 rounded-full bg-[#bf5fff]"></div>
                </div>

                <div class="neon-card rounded-xl p-5" style="border-color: rgba(191,95,255,0.15);">
                  <div class="flex flex-wrap items-start justify-between gap-2 mb-2">
                    <h4 class="font-bold text-[#e2f0ff]">{{ edu.degree }}</h4>
                    <span class="font-mono text-[10px] px-2 py-0.5 rounded bg-[#bf5fff]/10 text-[#bf5fff]">
                      {{ edu.period }}
                    </span>
                  </div>
                  <p class="font-mono text-sm text-[#bf5fff] mb-2">{{ edu.institution }}</p>
                  <p class="text-sm text-[#6b8cad] leading-relaxed mb-3">{{ edu.description }}</p>
                  <div class="flex flex-wrap gap-2">
                    <span
                      v-for="tag in edu.tags"
                      :key="tag"
                      class="px-2 py-0.5 text-[10px] font-mono rounded border border-[rgba(191,95,255,0.2)] text-[#bf5fff]/70"
                    >{{ tag }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- Organisasi / Extra -->
          <h3 class="font-mono text-sm text-[#ffd700] mt-12 mb-8 flex items-center gap-2">
            <span class="w-4 h-px bg-[#ffd700]"></span>
            Aktivitas &amp; Organisasi
          </h3>
          <div class="space-y-4">
            <div
              v-for="(org, idx) in organizations"
              :key="idx"
              class="flex items-start gap-4 p-4 rounded-xl bg-[#0a1628] border border-[rgba(255,215,0,0.1)] hover:border-[rgba(255,215,0,0.3)] transition-all duration-200"
            >
              <span class="text-2xl">{{ org.icon }}</span>
              <div>
                <p class="font-bold text-sm text-[#e2f0ff]">{{ org.name }}</p>
                <p class="font-mono text-[10px] text-[#ffd700]">{{ org.role }} · {{ org.period }}</p>
                <p class="text-xs text-[#6b8cad] mt-1">{{ org.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ExperienceSection',
  data() {
    return {
      experiences: [
        {
          role: 'Mobile Developer Intern',
          company: 'Program Magang',
          period: '2025',
          description:
            'Mengembangkan aplikasi mobile QMas-M menggunakan Flutter. Berkolaborasi dengan tim dalam proses pengembangan fitur dan integrasi dengan API backend.',
          tags: ['Flutter', 'Dart', 'REST API', 'Git'],
        },
        {
          role: 'Fullstack Developer',
          company: 'Proyek Kuliah',
          period: '2022 – 2024',
          description:
            'Membangun berbagai proyek kuliah mulai dari aplikasi e-voting, landing page, hingga admin dashboard sebagai bagian dari pembelajaran fullstack development.',
          tags: ['Vue', 'Golang', 'MySQL', 'Tailwind CSS'],
        },
      ],
      educations: [
        {
          degree: 'S1 Teknik Informatika',
          institution: 'Universitas Muhammadiyah Malang',
          period: '2022 – Sekarang',
          description:
            'Fokus pada rekayasa perangkat lunak dan pengembangan sistem. Aktif mengerjakan proyek akademik dan praktis di bidang web dan mobile development.',
          tags: ['Software Engineering', 'Informatika', 'RPL'],
        },
        {
          degree: 'SMA / Sederajat',
          institution: 'Madrasah Aliyah Unggulan Amanatul Qur`an',
          period: '2019 - 2022',
          description:
            'Menempuh pendidikan di pondok pesantren dengan kurikulum berbasis agama dan umum. Aktif dalam kegiatan ekstrakurikuler dan organisasi siswa.',
          tags: ['IPS'],
        },
      ],
      organizations: [
        {
          icon: '🤖',
          name: 'Anggota Robotika UMM',
          role: 'Divisi KRBAI',
          period: '2023 – 2025',
          description: 'Bergabung dalam tim robotika untuk mengembangkan kemampuan dalam bidang kecerdasan buatan dan otomasi. Berpartisipasi dalam kompetisi robot tingkat universitas.',
        },
        {
          icon: '🏆',
          name: 'Kontes Robot Indonesia',
          role: 'Peserta Divisi KRBAI(Kontes Robot Bawah Air Indonesia)',
          period: '2024',
          description: 'Mengikuti kompetisi robot bawah air tingkat nasional. Berkontribusi dalam desain dan pemrograman robot untuk menyelesaikan tantangan yang diberikan dalam kompetisi.',
        },
      ],
    }
  },
}
</script>
