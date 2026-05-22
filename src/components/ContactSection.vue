<template>
  <section id="kontak" class="py-24 px-6">
    <div class="max-w-6xl mx-auto">
      <!-- Header -->
      <div class="mb-16">
        <p class="font-mono text-[#00f5ff] text-sm mb-2">// 05. contact</p>
        <h2 class="text-4xl font-black text-[#e2f0ff]">Hubungi <span class="gradient-text">Saya</span></h2>
        <div class="mt-3 w-16 h-0.5 bg-gradient-to-r from-[#00f5ff] to-transparent"></div>
      </div>

      <div class="grid lg:grid-cols-2 gap-12 items-start">
        <!-- Left: message -->
        <div class="space-y-6">
          <p class="text-[#8fafc7] leading-relaxed text-lg">
            Saya terbuka untuk peluang kolaborasi, proyek freelance, maupun diskusi seputar
            <span class="text-[#00f5ff]">software engineering</span> dan
            <span class="text-[#00ff88]">pengembangan aplikasi</span>.
            Jangan ragu untuk menghubungi saya!
          </p>

          <div class="neon-card rounded-xl p-6 font-mono text-sm space-y-3">
            <div class="flex gap-2">
              <span class="text-[#00ff88]">hsdiqi@dev</span>
              <span class="text-[#6b8cad]">~$</span>
              <span class="text-[#e2f0ff]">ping hsdiqi</span>
            </div>
            <p class="text-[#6b8cad] pl-4">
              Respons biasanya dalam <span class="text-[#00f5ff]">24–48 jam</span>
            </p>
            <div class="flex items-center gap-2 pl-4">
              <span class="w-2 h-2 rounded-full bg-[#00ff88] animate-pulse"></span>
              <span class="text-[#00ff88]">Status: Online &amp; Aktif</span>
            </div>
          </div>

          <!-- Contact cards -->
          <div class="space-y-3">
            <a
              v-for="contact in contacts"
              :key="contact.label"
              :href="contact.href"
              target="_blank"
              rel="noopener"
              class="flex items-center gap-4 p-4 rounded-xl border transition-all duration-200 group"
              :class="contact.borderClass"
            >
              <div class="w-10 h-10 rounded-lg flex items-center justify-center text-lg flex-shrink-0"
                :class="contact.iconBg">
                <span v-html="contact.icon"></span>
              </div>
              <div class="flex-1">
                <p class="font-mono text-[10px] uppercase tracking-widest" :class="contact.labelClass">
                  {{ contact.label }}
                </p>
                <p class="text-sm text-[#e2f0ff] mt-0.5">{{ contact.value }}</p>
              </div>
              <svg class="w-4 h-4 text-[#6b8cad] group-hover:text-[#e2f0ff] group-hover:translate-x-1 transition-all duration-200" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7"/>
              </svg>
            </a>
          </div>
        </div>

        <!-- Right: form -->
        <div class="neon-card rounded-xl p-8">
          <h3 class="font-bold text-[#e2f0ff] mb-6 flex items-center gap-2">
            <span class="text-[#00f5ff]">#</span> Kirim Pesan
          </h3>

          <div class="space-y-5">
            <div>
              <label class="font-mono text-xs text-[#6b8cad] block mb-2">Nama</label>
              <input
                v-model="form.name"
                type="text"
                placeholder="Nama lengkap kamu"
                class="w-full bg-[#0a1628] border border-[rgba(0,245,255,0.15)] rounded-lg px-4 py-3 text-sm text-[#e2f0ff] placeholder-[#3a5a7a] focus:outline-none focus:border-[#00f5ff]/60 focus:ring-1 focus:ring-[#00f5ff]/20 transition-all duration-200 font-mono"
              />
            </div>

            <div>
              <label class="font-mono text-xs text-[#6b8cad] block mb-2">Email</label>
              <input
                v-model="form.email"
                type="email"
                placeholder="email@kamu.com"
                class="w-full bg-[#0a1628] border border-[rgba(0,245,255,0.15)] rounded-lg px-4 py-3 text-sm text-[#e2f0ff] placeholder-[#3a5a7a] focus:outline-none focus:border-[#00f5ff]/60 focus:ring-1 focus:ring-[#00f5ff]/20 transition-all duration-200 font-mono"
              />
            </div>

            <div>
              <label class="font-mono text-xs text-[#6b8cad] block mb-2">Subjek</label>
              <input
                v-model="form.subject"
                type="text"
                placeholder="Topik pesan kamu"
                class="w-full bg-[#0a1628] border border-[rgba(0,245,255,0.15)] rounded-lg px-4 py-3 text-sm text-[#e2f0ff] placeholder-[#3a5a7a] focus:outline-none focus:border-[#00f5ff]/60 focus:ring-1 focus:ring-[#00f5ff]/20 transition-all duration-200 font-mono"
              />
            </div>

            <div>
              <label class="font-mono text-xs text-[#6b8cad] block mb-2">Pesan</label>
              <textarea
                v-model="form.message"
                rows="5"
                placeholder="Tulis pesanmu di sini..."
                class="w-full bg-[#0a1628] border border-[rgba(0,245,255,0.15)] rounded-lg px-4 py-3 text-sm text-[#e2f0ff] placeholder-[#3a5a7a] focus:outline-none focus:border-[#00f5ff]/60 focus:ring-1 focus:ring-[#00f5ff]/20 transition-all duration-200 font-mono resize-none"
              ></textarea>
            </div>

            <button
              type="button"
              @click="sendMessage"
              :disabled="sending"
              class="w-full flex items-center justify-center gap-2 py-3 bg-[#00f5ff] text-[#050a0f] font-bold font-mono text-sm rounded-lg hover:bg-[#00d4e0] transition-all duration-200 glow-cyan disabled:opacity-50 disabled:cursor-not-allowed"
            >
              <span v-if="!sent && !sending">Kirim Pesan →</span>
              <span v-else-if="sending" class="flex items-center gap-2">
                <svg class="animate-spin w-4 h-4" fill="none" viewBox="0 0 24 24">
                  <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"/>
                  <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8v8z"/>
                </svg>
                Mengirim...
              </span>
              <span v-else class="flex items-center gap-2">✓ Pesan Terkirim!</span>
            </button>

            <p class="text-[10px] font-mono text-[#3a5a7a] text-center">
              * Form ini hanya demonstrasi — hubungi via email atau WhatsApp untuk komunikasi langsung.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ContactSection',
  data() {
    return {
      form: {
        name: '',
        email: '',
        subject: '',
        message: '',
      },
      sending: false,
      sent: false,
      contacts: [
        {
          label: 'Email',
          value: 'hasbi@example.com',
          href: 'mailto:hasbi@example.com',
          icon: '✉️',
          iconBg: 'bg-[#00f5ff]/10',
          labelClass: 'text-[#00f5ff]',
          borderClass: 'border-[rgba(0,245,255,0.15)] hover:border-[#00f5ff]/40 bg-[#0a1628]',
        },
        {
          label: 'WhatsApp',
          value: '+62 8xx-xxxx-xxxx',
          href: 'https://wa.me/6280000000000',
          icon: '💬',
          iconBg: 'bg-[#00ff88]/10',
          labelClass: 'text-[#00ff88]',
          borderClass: 'border-[rgba(0,255,136,0.15)] hover:border-[#00ff88]/40 bg-[#0a1628]',
        },
        {
          label: 'GitHub',
          value: 'github.com/hsdiqi',
          href: 'https://github.com/hsdiqi',
          icon: '🐙',
          iconBg: 'bg-[#bf5fff]/10',
          labelClass: 'text-[#bf5fff]',
          borderClass: 'border-[rgba(191,95,255,0.15)] hover:border-[#bf5fff]/40 bg-[#0a1628]',
        },
        {
          label: 'LinkedIn',
          value: 'linkedin.com/in/hsdiqi',
          href: 'https://linkedin.com/in/hsdiqi',
          icon: '🔗',
          iconBg: 'bg-[#ffd700]/10',
          labelClass: 'text-[#ffd700]',
          borderClass: 'border-[rgba(255,215,0,0.15)] hover:border-[#ffd700]/40 bg-[#0a1628]',
        },
      ],
    }
  },
  methods: {
    sendMessage() {
      if (!this.form.name || !this.form.email || !this.form.message) return
      this.sending = true
      setTimeout(() => {
        this.sending = false
        this.sent = true
        this.form = { name: '', email: '', subject: '', message: '' }
        setTimeout(() => {
          this.sent = false
        }, 4000)
      }, 1500)
    },
  },
}
</script>
