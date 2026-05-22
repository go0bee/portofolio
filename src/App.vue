<template>
  <div class="relative min-h-screen bg-[#050a0f]">
    <!-- Noise overlay -->
    <div class="noise-overlay"></div>

    <!-- Ambient background blobs -->
    <div class="fixed inset-0 pointer-events-none overflow-hidden z-0">
      <div class="absolute top-[-20%] left-[-10%] w-[600px] h-[600px] rounded-full opacity-[0.04]"
        style="background: radial-gradient(circle, #00f5ff, transparent 70%)"></div>
      <div class="absolute bottom-[-20%] right-[-10%] w-[700px] h-[700px] rounded-full opacity-[0.04]"
        style="background: radial-gradient(circle, #00ff88, transparent 70%)"></div>
      <div class="absolute top-[40%] left-[40%] w-[400px] h-[400px] rounded-full opacity-[0.03]"
        style="background: radial-gradient(circle, #bf5fff, transparent 70%)"></div>
    </div>

    <!-- Grid background -->
    <div class="fixed inset-0 grid-bg z-0 pointer-events-none"></div>

    <!-- Content -->
    <div class="relative z-10">
      <Navbar />
      <main>
        <HeroSection />
        <AboutSection />
        <SkillsSection />
        <ProjectsSection />
        <ExperienceSection />
        <ContactSection />
      </main>
      <Footer />
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    HeroSection,
    AboutSection,
    SkillsSection,
    ProjectsSection,
    ExperienceSection,
    ContactSection,
    Footer,
  },
}
</script>
