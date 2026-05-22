<template>
  <section id="proyek" class="py-24 px-6">
    <div class="max-w-6xl mx-auto">
      <!-- Header -->
      <div class="mb-16">
        <p class="font-mono text-[#00f5ff] text-sm mb-2">// 03. projects</p>
        <h2 class="text-4xl font-black text-[#e2f0ff]">Proyek <span class="gradient-text">Terbaru</span></h2>
        <div class="mt-3 w-16 h-0.5 bg-gradient-to-r from-[#00f5ff] to-transparent"></div>
      </div>

      <!-- Filter tabs -->
      <div class="flex flex-wrap gap-3 mb-10">
        <button
          v-for="filter in filters"
          :key="filter"
          @click="activeFilter = filter"
          :class="[
            'px-4 py-1.5 rounded font-mono text-sm transition-all duration-200',
            activeFilter === filter
              ? 'bg-[#00f5ff] text-[#050a0f] font-bold'
              : 'border border-[rgba(0,245,255,0.2)] text-[#6b8cad] hover:border-[#00f5ff]/50 hover:text-[#00f5ff]'
          ]"
        >
          {{ filter }}
        </button>
      </div>

      <!-- Project grid -->
      <div class="grid md:grid-cols-2 xl:grid-cols-3 gap-6">
        <div
          v-for="project in filteredProjects"
          :key="project.id"
          class="neon-card rounded-xl overflow-hidden group flex flex-col"
        >
          <!-- Project header / banner -->
          <div class="relative h-36 flex items-center justify-center overflow-hidden"
            :class="bannerBg(project.categoryColor)">
            <div class="absolute inset-0 opacity-20"
              style="background-image: repeating-linear-gradient(45deg, transparent, transparent 10px, rgba(255,255,255,0.05) 10px, rgba(255,255,255,0.05) 11px)"></div>
            <span class="text-5xl relative z-10 group-hover:scale-110 transition-transform duration-300">{{ project.icon }}</span>
            <!-- Category badge -->
            <span
              class="absolute top-3 right-3 px-2 py-1 rounded text-[10px] font-mono font-bold"
              :class="categoryBadge(project.categoryColor)"
            >
              {{ project.category }}
            </span>
          </div>

          <!-- Content -->
          <div class="p-6 flex flex-col flex-1">
            <h3 class="text-lg font-bold text-[#e2f0ff] mb-2 group-hover:text-[#00f5ff] transition-colors duration-200">
              {{ project.title }}
            </h3>
            <p class="text-sm text-[#6b8cad] leading-relaxed mb-4 flex-1">
              {{ project.description }}
            </p>

            <!-- Stack tags -->
            <div class="flex flex-wrap gap-2 mb-4">
              <span
                v-for="tech in project.stack"
                :key="tech"
                class="px-2 py-0.5 text-xs font-mono rounded border border-[rgba(0,245,255,0.15)] text-[#8fafc7]"
              >
                {{ tech }}
              </span>
            </div>

            <!-- Links -->
            <div class="flex items-center gap-4 pt-2 border-t border-[rgba(0,245,255,0.08)]">
              <a
                :href="project.github"
                target="_blank"
                rel="noopener"
                class="flex items-center gap-1.5 font-mono text-xs text-[#6b8cad] hover:text-[#00f5ff] transition-colors duration-200"
              >
                <svg class="w-3.5 h-3.5" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"/>
                </svg>
                Source
              </a>
              <a
                v-if="project.demo"
                :href="project.demo"
                target="_blank"
                rel="noopener"
                class="flex items-center gap-1.5 font-mono text-xs text-[#6b8cad] hover:text-[#00ff88] transition-colors duration-200"
              >
                <svg class="w-3.5 h-3.5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"/>
                </svg>
                Demo
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { projects } from '../data/projects.js'

export default {
  name: 'ProjectsSection',
  data() {
    return {
      projects,
      activeFilter: 'Semua',
      filters: ['Semua', 'Mobile App', 'Web App', 'Website'],
    }
  },
  computed: {
    filteredProjects() {
      if (this.activeFilter === 'Semua') return this.projects
      return this.projects.filter(p => p.category === this.activeFilter)
    },
  },
  methods: {
    bannerBg(color) {
      const map = {
        purple: 'bg-gradient-to-br from-[#1a0a2e] to-[#0d0618]',
        blue: 'bg-gradient-to-br from-[#0a1a30] to-[#050e1a]',
        green: 'bg-gradient-to-br from-[#0a2010] to-[#050e08]',
        cyan: 'bg-gradient-to-br from-[#0a2028] to-[#050e14]',
        orange: 'bg-gradient-to-br from-[#2a1400] to-[#0f0800]',
      }
      return map[color] || 'bg-[#0d1f35]'
    },
    categoryBadge(color) {
      const map = {
        purple: 'bg-[#bf5fff]/20 text-[#bf5fff] border border-[#bf5fff]/30',
        blue: 'bg-[#0066ff]/20 text-[#6699ff] border border-[#6699ff]/30',
        green: 'bg-[#00ff88]/20 text-[#00ff88] border border-[#00ff88]/30',
        cyan: 'bg-[#00f5ff]/20 text-[#00f5ff] border border-[#00f5ff]/30',
        orange: 'bg-[#ff9500]/20 text-[#ff9500] border border-[#ff9500]/30',
      }
      return map[color] || 'bg-[#00f5ff]/20 text-[#00f5ff]'
    },
  },
}
</script>
