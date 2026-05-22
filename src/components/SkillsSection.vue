<template>
  <section id="keahlian" class="py-24 px-6 bg-[#050e1a]">
    <div class="max-w-6xl mx-auto">
      <!-- Header -->
      <div class="mb-16">
        <p class="font-mono text-[#00f5ff] text-sm mb-2">// 02. skills</p>
        <h2 class="text-4xl font-black text-[#e2f0ff]">Keahlian <span class="gradient-text">Teknis</span></h2>
        <div class="mt-3 w-16 h-0.5 bg-gradient-to-r from-[#00f5ff] to-transparent"></div>
      </div>

      <!-- Skill groups grid -->
      <div class="grid md:grid-cols-2 xl:grid-cols-3 gap-6">
        <div
          v-for="group in skillGroups"
          :key="group.category"
          class="neon-card rounded-xl p-6 group transition-all duration-300"
          :class="cardHoverClass(group.color)"
        >
          <!-- Group header -->
          <div class="flex items-center gap-3 mb-6">
            <div
              class="w-10 h-10 rounded-lg flex items-center justify-center text-lg"
              :class="iconBgClass(group.color)"
            >
              {{ group.icon }}
            </div>
            <div>
              <h3 class="font-bold text-[#e2f0ff]">{{ group.category }}</h3>
              <p class="font-mono text-[10px] text-[#6b8cad]">{{ group.skills.length }} teknologi</p>
            </div>
          </div>

          <!-- Skills list -->
          <div class="space-y-3">
            <div
              v-for="skill in group.skills"
              :key="skill.name"
              class="flex items-center justify-between gap-3 px-3 py-2.5 rounded-lg bg-[#0a1628] border border-[rgba(0,245,255,0.06)] hover:border-[rgba(0,245,255,0.15)] transition-all duration-200"
            >
              <!-- Skill name with dot indicator -->
              <div class="flex items-center gap-2.5">
                <span
                  class="w-1.5 h-1.5 rounded-full flex-shrink-0"
                  :class="dotClass(group.color)"
                ></span>
                <span class="font-mono text-sm text-[#c8dff0]">{{ skill.name }}</span>
              </div>

              <!-- Year badge -->
              <div
                class="flex items-center gap-1.5 px-2.5 py-1 rounded-full border font-mono text-[10px] flex-shrink-0"
                :class="yearBadgeClass(group.color)"
              >
                <svg class="w-2.5 h-2.5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                  <rect x="3" y="4" width="18" height="18" rx="2" ry="2"/>
                  <line x1="16" y1="2" x2="16" y2="6"/>
                  <line x1="8" y1="2" x2="8" y2="6"/>
                  <line x1="3" y1="10" x2="21" y2="10"/>
                </svg>
                {{ skill.label }}
              </div>
            </div>
          </div>

          <!-- Years active summary -->
          <div class="mt-4 pt-4 border-t border-[rgba(0,245,255,0.06)]">
            <p class="font-mono text-[10px] text-[#3a5a7a]">
              Paling lama digunakan sejak
              <span :class="accentTextClass(group.color)">
                {{ oldestYear(group.skills) }}
              </span>
            </p>
          </div>
        </div>
      </div>

      <!-- Tech badge cloud -->
      <div class="mt-12 pt-12 border-t border-[rgba(0,245,255,0.08)]">
        <p class="font-mono text-xs text-[#6b8cad] mb-6 text-center">// Semua teknologi yang pernah digunakan</p>
        <div class="flex flex-wrap justify-center gap-3">
          <span
            v-for="badge in allTech"
            :key="badge"
            class="px-3 py-1.5 rounded font-mono text-xs border border-[rgba(0,245,255,0.15)] text-[#8fafc7] hover:border-[#00f5ff]/50 hover:text-[#00f5ff] transition-all duration-200 cursor-default"
          >
            {{ badge }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { skillGroups } from '../data/skills.js'

export default {
  name: 'SkillsSection',
  data() {
    return {
      skillGroups,
      allTech: [
        'Vue.js', 'Tailwind CSS', 'Bootstrap', 'Golang', 'Express.js',
        'Laravel', 'Flutter', 'MySQL', 'PostgreSQL', 'Docker',
        'Git', 'GitHub', 'Figma', 'Postman', 'Linux', 'REST API',
        'JSON', 'Bash', 'VS Code',
      ],
    }
  },
  methods: {
    oldestYear(skills) {
      return Math.min(...skills.map(s => s.since))
    },
    cardHoverClass(color) {
      const map = {
        cyan: 'hover:border-[#00f5ff]/40',
        green: 'hover:border-[#00ff88]/40',
        purple: 'hover:border-[#bf5fff]/40',
        yellow: 'hover:border-[#ffd700]/40',
        orange: 'hover:border-[#ff9500]/40',
      }
      return map[color] || ''
    },
    iconBgClass(color) {
      const map = {
        cyan: 'bg-[#00f5ff]/10 text-[#00f5ff]',
        green: 'bg-[#00ff88]/10 text-[#00ff88]',
        purple: 'bg-[#bf5fff]/10 text-[#bf5fff]',
        yellow: 'bg-[#ffd700]/10 text-[#ffd700]',
        orange: 'bg-[#ff9500]/10 text-[#ff9500]',
      }
      return map[color] || ''
    },
    dotClass(color) {
      const map = {
        cyan: 'bg-[#00f5ff]',
        green: 'bg-[#00ff88]',
        purple: 'bg-[#bf5fff]',
        yellow: 'bg-[#ffd700]',
        orange: 'bg-[#ff9500]',
      }
      return map[color] || 'bg-[#00f5ff]'
    },
    yearBadgeClass(color) {
      const map = {
        cyan: 'border-[#00f5ff]/25 text-[#00f5ff]/80 bg-[#00f5ff]/5',
        green: 'border-[#00ff88]/25 text-[#00ff88]/80 bg-[#00ff88]/5',
        purple: 'border-[#bf5fff]/25 text-[#bf5fff]/80 bg-[#bf5fff]/5',
        yellow: 'border-[#ffd700]/25 text-[#ffd700]/80 bg-[#ffd700]/5',
        orange: 'border-[#ff9500]/25 text-[#ff9500]/80 bg-[#ff9500]/5',
      }
      return map[color] || ''
    },
    accentTextClass(color) {
      const map = {
        cyan: 'text-[#00f5ff]',
        green: 'text-[#00ff88]',
        purple: 'text-[#bf5fff]',
        yellow: 'text-[#ffd700]',
        orange: 'text-[#ff9500]',
      }
      return map[color] || 'text-[#00f5ff]'
    },
  },
}
</script>
