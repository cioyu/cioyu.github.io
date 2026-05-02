<script setup>
import { ref } from 'vue'

const currentYear = ref(new Date().getFullYear())

function scrollToMain() {
  const el = document.querySelector('.main')
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}

const linuxJourney = [
  { distro: 'Ubuntu', desc: '安装的第一个发行版', icon: '🐧' },
  { distro: 'openEuler', desc: '学校 Linux 课装的（虚拟机）', icon: '🖥️' },
  { distro: 'Arch Linux', desc: '看 Shorin 的 niri 感觉很炫酷，跟着搭建了', icon: '🚀' },
  { distro: 'Fedora', desc: 'Arch 分区分小了，于是重装了', icon: '🔄' },
  { distro: 'CachyOS', desc: '打算装 KDE 版 Fedora 结果黑屏，换到了 Cachy', icon: '⚡' },
]

const contacts = [
  { name: 'GitHub', url: 'https://github.com/cioyu', icon: '💻' },
  { name: 'Bilibili', url: 'https://space.bilibili.com/1928417915s', icon: '📺' },
  { name: 'YouTube', url: 'https://www.youtube.com/channel/UC_WmZj9i7MZV899g1iunwdA', icon: '🎬' },
  { name: 'Email', url: 'mailto:cioyu32@gmail.com', icon: '✉️', sub: 'cioyu32@gmail.com' },
]
</script>

<template>
  <div class="page-wrapper">
    <!-- ===== Hero ===== -->
    <header class="hero">
      <div class="hero-bg"></div>

      <!-- Floating sparkles -->
      <div class="sparkle-container">
        <span v-for="n in 12" :key="n" class="sparkle" :style="{ '--s': n }">✦</span>
      </div>

      <div class="hero-foreground">
        <!-- Decorative circles -->
        <div class="deco-circle c1"></div>
        <div class="deco-circle c2"></div>
        <div class="deco-circle c3"></div>

        <div class="hero-content">
          <div class="avatar-ring">
            <div class="avatar">C</div>
          </div>
          <h1 class="hero-title">Cioyu 的<br>个人博客</h1>
          <p class="hero-subtitle">✦ 网络专业学生 ✦</p>
          <div class="hero-cta">
            <span class="scroll-hint" @click="scrollToMain">↓ 往下看看</span>
          </div>
        </div>
      </div>

      <!-- Wave divider -->
      <div class="wave-divider">
        <svg viewBox="0 0 1440 80" preserveAspectRatio="none">
          <path d="M0,40 C360,80 720,0 1080,40 C1260,60 1350,50 1440,40 L1440,80 L0,80 Z" fill="var(--bg)"/>
        </svg>
      </div>
    </header>

    <!-- ===== Main ===== -->
    <main class="main">
      <div class="container">
        <!-- About -->
        <section class="card about-card">
          <div class="card-accent"></div>
          <h2 class="section-title">
            <span class="title-icon">🌸</span> 关于我
          </h2>
          <p class="about-text">
            网络专业的学生，喜欢看小说，偶尔看下番，玩玩游戏。
            目前正在 Web 前端领域探索，同时也在折腾 Linux 的道路上越走越远。
          </p>
          <div class="about-tags">
            <span class="about-tag">🎮 游戏</span>
            <span class="about-tag">📖 小说</span>
            <span class="about-tag">🐧 Linux</span>
            <span class="about-tag">💻 前端</span>
          </div>
        </section>

        <!-- Linux Journey -->
        <section class="card journey-card">
          <div class="card-accent accent-pink"></div>
          <h2 class="section-title">
            <span class="title-icon">🐧</span> 折腾 GNU/Linux 的历程
          </h2>
          <div class="timeline">
            <div
              v-for="(item, index) in linuxJourney"
              :key="item.distro"
              class="timeline-item"
              :style="{ '--i': index }"
            >
              <div class="timeline-dot">{{ item.icon }}</div>
              <div class="timeline-body">
                <h3 class="timeline-title">{{ item.distro }}</h3>
                <p class="timeline-desc">{{ item.desc }}</p>
              </div>
            </div>
          </div>
        </section>

        <!-- Learning -->
        <section class="card learning-card">
          <div class="card-accent accent-purple"></div>
          <h2 class="section-title">
            <span class="title-icon">📚</span> 学习方向
          </h2>
          <div class="learning-grid">
            <div class="learning-item current">
              <span class="learning-label">NOW</span>
              <div class="learning-tags">
                <span class="tag">HTML</span>
                <span class="tag">CSS</span>
                <span class="tag">JavaScript</span>
                <span class="tag">Vue</span>
              </div>
              <p class="learning-desc">Web 前端开发</p>
            </div>
            <div class="learning-item future">
              <span class="learning-label label-orange">NEXT</span>
              <div class="learning-tags">
                <span class="tag">C</span>
                <span class="tag">Rust</span>
                <span class="tag">PHP</span>
              </div>
              <p class="learning-desc">深入系统编程与后端</p>
            </div>
          </div>
        </section>

        <!-- Contact -->
        <section class="card contact-card">
          <div class="card-accent accent-blue"></div>
          <h2 class="section-title">
            <span class="title-icon">💫</span> 联系方式
          </h2>
          <div class="contact-grid">
            <a
              v-for="c in contacts"
              :key="c.name"
              :href="c.url"
              class="contact-item"
              target="_blank"
              rel="noopener noreferrer"
            >
              <span class="contact-icon">{{ c.icon }}</span>
              <span class="contact-name">{{ c.name }}</span>
              <span v-if="c.sub" class="contact-sub">{{ c.sub }}</span>
            </a>
          </div>
        </section>
      </div>
    </main>

    <!-- ===== Footer ===== -->
    <footer class="footer">
      <div class="container">
        <div class="footer-stars">✦ ✦ ✦</div>
        <p>&copy; {{ currentYear }} Cioyu </p>
      </div>
    </footer>
  </div>
</template>

<style>
/* ===== Global Reset ===== */
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --pink: #f472b6;
  --pink-light: #f9a8d4;
  --pink-lighter: #fce7f3;
  --purple: #a78bfa;
  --purple-light: #c4b5fd;
  --blue: #60a5fa;
  --blue-light: #93c5fd;
  --orange: #fb923c;
  --bg: #faf5ff;
  --card-bg: #ffffffcc;
  --text: #1e1b4b;
  --text-secondary: #6b21a8;
  --text-muted: #a78bfa;
  --radius: 20px;
  --shadow: 0 4px 16px rgba(168,85,247,.12);
  --shadow-lg: 0 8px 30px rgba(168,85,247,.18);
  --font: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Noto Sans SC', sans-serif;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: var(--font);
  background: var(--bg);
  color: var(--text);
  line-height: 1.8;
  -webkit-font-smoothing: antialiased;
  overflow-x: hidden;
}

a {
  text-decoration: none;
  color: inherit;
}

::selection {
  background: var(--pink-light);
  color: #fff;
}
</style>

<style scoped>
/* ============================
   Layout
   ============================ */
.page-wrapper {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.container {
  max-width: 720px;
  margin: 0 auto;
  padding: 0 20px;
}

/* ============================
   Hero
   ============================ */
.hero {
  position: relative;
  min-height: 70vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg,
    #2e1065 0%,
    #6b21a8 20%,
    #a21caf 40%,
    #db2777 60%,
    #e11d48 80%,
    #be123c 100%
  );
  z-index: 0;
}

.hero-bg::after {
  content: '';
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse 70% 50% at 30% 30%, rgba(216,180,254,.25) 0%, transparent 60%),
    radial-gradient(ellipse 60% 40% at 70% 70%, rgba(249,168,212,.2) 0%, transparent 50%),
    radial-gradient(ellipse 50% 40% at 50% 100%, rgba(147,197,253,.15) 0%, transparent 50%);
}

.hero-foreground {
  position: relative;
  z-index: 2;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* ===== Decorative Circles ===== */
.deco-circle {
  position: absolute;
  border-radius: 50%;
  opacity: .15;
  animation: floatCircle 8s ease-in-out infinite;
}

.c1 {
  width: 300px;
  height: 300px;
  background: var(--pink-light);
  top: -10%;
  left: -5%;
  animation-delay: 0s;
}

.c2 {
  width: 200px;
  height: 200px;
  background: var(--blue-light);
  bottom: 10%;
  right: -3%;
  animation-delay: -3s;
}

.c3 {
  width: 150px;
  height: 150px;
  background: var(--purple-light);
  top: 40%;
  right: 15%;
  animation-delay: -5s;
}

@keyframes floatCircle {
  0%, 100% { transform: translate(0,0) scale(1); }
  33%      { transform: translate(20px,-20px) scale(1.05); }
  66%      { transform: translate(-10px,15px) scale(.95); }
}

/* ===== Sparkles ===== */
.sparkle-container {
  position: absolute;
  inset: 0;
  z-index: 1;
  pointer-events: none;
  overflow: hidden;
}

.sparkle {
  position: absolute;
  color: rgba(255,255,255,.6);
  font-size: calc(10px + var(--s) * 2px);
  animation: sparkleFloat 6s ease-in-out infinite;
  animation-delay: calc(var(--s) * -.5s);
  opacity: 0;
}

.sparkle:nth-child(1)  { top: 8%;  left: 10%; }
.sparkle:nth-child(2)  { top: 15%; left: 30%; font-size: 14px; }
.sparkle:nth-child(3)  { top: 5%;  left: 55%; }
.sparkle:nth-child(4)  { top: 20%; left: 80%; font-size: 12px; }
.sparkle:nth-child(5)  { top: 35%; left: 5%; }
.sparkle:nth-child(6)  { top: 45%; left: 90%; font-size: 16px; }
.sparkle:nth-child(7)  { top: 55%; left: 20%; font-size: 11px; }
.sparkle:nth-child(8)  { top: 65%; left: 70%; }
.sparkle:nth-child(9)  { top: 75%; left: 40%; font-size: 13px; }
.sparkle:nth-child(10) { top: 30%; left: 50%; font-size: 9px; }
.sparkle:nth-child(11) { top: 50%; left: 45%; }
.sparkle:nth-child(12) { top: 70%; left: 85%; font-size: 15px; }

@keyframes sparkleFloat {
  0%, 100% {
    opacity: 0;
    transform: translateY(0) scale(.5);
  }
  25% {
    opacity: .8;
    transform: translateY(-20px) scale(1);
  }
  50% {
    opacity: .3;
    transform: translateY(-40px) scale(.7);
  }
  75% {
    opacity: .6;
    transform: translateY(-10px) scale(1.1);
  }
}

/* ===== Hero Content ===== */
.hero-content {
  text-align: center;
  color: #fff;
  padding: 60px 20px;
  animation: heroFadeIn 1s ease-out;
}

@keyframes heroFadeIn {
  from { opacity: 0; transform: translateY(30px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* Avatar */
.avatar-ring {
  width: 100px;
  height: 100px;
  margin: 0 auto 24px;
  border-radius: 50%;
  padding: 4px;
  background: conic-gradient(var(--pink-light), var(--purple-light), var(--blue-light), var(--pink-light));
  animation: spinRing 6s linear infinite;
}

@keyframes spinRing {
  to { transform: rotate(360deg); }
}

.avatar {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background: linear-gradient(135deg, #6b21a8, #db2777);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 36px;
  font-weight: 800;
  color: #fff;
  transition: transform .3s;
}

.avatar:hover {
  transform: scale(1.06);
}

/* Title */
.hero-title {
  font-size: clamp(2rem, 6vw, 3.5rem);
  font-weight: 800;
  letter-spacing: -.03em;
  line-height: 1.2;
  margin-bottom: 12px;
  text-shadow: 0 2px 20px rgba(0,0,0,.2);
}

/* Subtitle */
.hero-subtitle {
  font-size: 1.05rem;
  opacity: .85;
  font-weight: 400;
  letter-spacing: .02em;
}

/* CTA */
.hero-cta {
  margin-top: 48px;
}

.scroll-hint {
  display: inline-block;
  padding: 8px 24px;
  border-radius: 40px;
  background: rgba(255,255,255,.12);
  backdrop-filter: blur(8px);
  border: 1px solid rgba(255,255,255,.2);
  font-size: .88rem;
  color: rgba(255,255,255,.8);
  animation: hintBounce 2.5s infinite;
  cursor: pointer;
  transition: background .3s;
}

.scroll-hint:hover {
  background: rgba(255,255,255,.2);
}

@keyframes hintBounce {
  0%, 100% { transform: translateY(0); }
  50%      { transform: translateY(6px); }
}

/* ===== Wave Divider ===== */
.wave-divider {
  position: absolute;
  bottom: -1px;
  left: 0;
  width: 100%;
  line-height: 0;
  z-index: 2;
}

.wave-divider svg {
  display: block;
  width: 100%;
  height: 60px;
}

/* ============================
   Main
   ============================ */
.main {
  flex: 1;
  padding: 20px 0 60px;
  position: relative;
  z-index: 1;
}

/* ============================
   Card
   ============================ */
.card {
  position: relative;
  background: var(--card-bg);
  backdrop-filter: blur(12px);
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  padding: 32px;
  margin-bottom: 28px;
  border: 1px solid rgba(168,85,247,.08);
  overflow: hidden;
  transition: box-shadow .3s, transform .3s;
}

.card:hover {
  box-shadow: var(--shadow-lg);
  transform: translateY(-3px);
}

.card-accent {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(90deg, var(--pink), var(--purple));
  border-radius: var(--radius) var(--radius) 0 0;
}

.accent-pink {
  background: linear-gradient(90deg, var(--pink), var(--pink-light));
}

.accent-purple {
  background: linear-gradient(90deg, var(--purple), var(--purple-light));
}

.accent-blue {
  background: linear-gradient(90deg, var(--blue), var(--blue-light));
}

.section-title {
  font-size: 1.2rem;
  font-weight: 700;
  margin-bottom: 16px;
  color: var(--text);
  display: flex;
  align-items: center;
  gap: 8px;
}

.title-icon {
  font-size: 1.3rem;
}

/* ============================
   About
   ============================ */
.about-text {
  color: var(--text-secondary);
  font-size: 1rem;
  line-height: 1.9;
  opacity: .9;
}

.about-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 16px;
}

.about-tag {
  display: inline-block;
  font-size: .82rem;
  padding: 4px 14px;
  border-radius: 20px;
  background: linear-gradient(135deg, var(--pink-lighter), #f3e8ff);
  color: var(--text-secondary);
  font-weight: 500;
  border: 1px solid rgba(168,85,247,.1);
}

/* ============================
   Timeline
   ============================ */
.timeline {
  position: relative;
  padding-left: 40px;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 15px;
  top: 8px;
  bottom: 8px;
  width: 2px;
  background: linear-gradient(to bottom, var(--pink), var(--purple), var(--blue));
  border-radius: 2px;
}

.timeline-item {
  position: relative;
  padding-bottom: 24px;
  animation: slideUp .5s ease-out both;
  animation-delay: calc(var(--i) * .1s);
}

.timeline-item:last-child { padding-bottom: 0; }

@keyframes slideUp {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}

.timeline-dot {
  position: absolute;
  left: -40px;
  top: 2px;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background: #fff;
  border: 2px solid var(--purple-light);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 15px;
  z-index: 1;
  box-shadow: 0 0 0 4px rgba(168,85,247,.08);
}

.timeline-body {
  background: linear-gradient(135deg, #faf5ff, #fdf2f8);
  border-radius: 14px;
  padding: 14px 20px;
  border: 1px solid rgba(168,85,247,.06);
}

.timeline-title {
  font-size: 1rem;
  font-weight: 700;
  background: linear-gradient(135deg, var(--pink), var(--purple));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 4px;
}

.timeline-desc {
  font-size: .9rem;
  color: var(--text-secondary);
  line-height: 1.6;
  opacity: .85;
}

/* ============================
   Learning
   ============================ */
.learning-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.learning-item {
  border-radius: 14px;
  padding: 22px;
  border: 1px solid rgba(168,85,247,.08);
}

.learning-item.current {
  background: linear-gradient(135deg, #fdf2f8, #fce7f3);
}

.learning-item.future {
  background: linear-gradient(135deg, #fff7ed, #ffedd5);
}

.learning-label {
  display: inline-block;
  font-size: .7rem;
  font-weight: 700;
  letter-spacing: .06em;
  padding: 3px 12px;
  border-radius: 20px;
  background: linear-gradient(135deg, var(--pink), var(--purple));
  color: #fff;
  margin-bottom: 10px;
}

.label-orange {
  background: linear-gradient(135deg, var(--orange), #fbbf24);
}

.learning-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-bottom: 10px;
}

.tag {
  display: inline-block;
  font-size: .82rem;
  font-weight: 500;
  padding: 3px 10px;
  border-radius: 8px;
  background: rgba(255,255,255,.75);
  color: var(--text);
  backdrop-filter: blur(4px);
}

.learning-desc {
  font-size: .85rem;
  color: var(--text-secondary);
  opacity: .8;
}

/* ============================
   Contact
   ============================ */
.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 12px;
}

.contact-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  padding: 22px 12px;
  border-radius: 14px;
  background: linear-gradient(135deg, #faf5ff, #fdf2f8);
  border: 1px solid rgba(168,85,247,.06);
  transition: background .3s, transform .3s, box-shadow .3s;
}

.contact-item:hover {
  background: linear-gradient(135deg, #f3e8ff, #fce7f3);
  transform: translateY(-5px);
  box-shadow: var(--shadow-lg);
}

.contact-icon {
  font-size: 1.8rem;
}

.contact-name {
  font-weight: 600;
  font-size: .95rem;
  color: var(--text);
}

.contact-sub {
  font-size: .75rem;
  color: var(--text-muted);
  word-break: break-all;
  text-align: center;
}

/* ============================
   Footer
   ============================ */
.footer {
  text-align: center;
  padding: 32px 0;
  color: var(--text-muted);
  font-size: .85rem;
}

.footer-stars {
  font-size: .9rem;
  letter-spacing: 6px;
  margin-bottom: 8px;
  opacity: .5;
}

/* ============================
   Responsive
   ============================ */
@media (max-width: 640px) {
  .card {
    padding: 24px 18px;
  }

  .learning-grid {
    grid-template-columns: 1fr;
  }

  .contact-grid {
    grid-template-columns: 1fr 1fr;
  }

  .timeline {
    padding-left: 36px;
  }

  .timeline-dot {
    left: -36px;
    width: 28px;
    height: 28px;
    font-size: 13px;
  }

  .hero {
    min-height: 60vh;
  }

  .wave-divider svg {
    height: 30px;
  }

  .avatar-ring {
    width: 80px;
    height: 80px;
  }

  .avatar {
    font-size: 28px;
  }
}
</style>
