<script setup>
import { ref } from 'vue'
import PathPage from './pages/PathPage.vue'

const activeTab = ref('Home')

const tabs = ['Home', 'Jobs', 'Path']

const jobs = [
  { icon: 'UX', title: 'Product Designer', team: 'Team Orbit', detail: 'Shape a calm, accessible interface for a climate-action tool.', tags: ['Figma', 'Research'], color: 'coral' },
  { icon: 'AI', title: 'ML Builder', team: 'Byte Bloom', detail: 'Prototype a lightweight matching engine for community skills.', tags: ['Python', 'NLP'], color: 'lime' },
  { icon: 'FE', title: 'Frontend Developer', team: 'Open Table', detail: 'Bring a friendly public-data dashboard to life in Vue.', tags: ['Vue', 'Data Viz'], color: 'blue' },
]

function switchTab(tab) {
  activeTab.value = tab
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>

<template>
  <div class="site-shell">
    <header class="nav-wrap">
      <button class="brand" aria-label="Go to Home" @click="switchTab('Home')">
        <span class="brand-mark">H<span>→</span></span>
        <span>HackShift</span>
      </button>

      <nav aria-label="Main navigation">
        <button
          v-for="tab in tabs"
          :key="tab"
          :class="{ active: activeTab === tab }"
          @click="switchTab(tab)"
        >
          {{ tab }}
        </button>
      </nav>

      <button class="join-btn" @click="switchTab('Jobs')">Join a team <span>↗</span></button>
    </header>

    <main>
      <section v-if="activeTab === 'Home'" class="page home-page">
        <div class="eyebrow"><span></span> Hackathon showcase · 48 hours</div>
        <div class="hero-grid">
          <div>
            <h1>Build the<br /><em>unexpected.</em></h1>
            <p class="hero-copy">A fast, friendly space for curious people to turn bold questions into working ideas.</p>
            <div class="hero-actions">
              <button class="primary" @click="switchTab('Jobs')">Find your team <span>→</span></button>
              <button class="text-btn" @click="switchTab('Path')">Explore career paths <span>↘</span></button>
            </div>
          </div>

          <div class="hero-art" aria-hidden="true">
            <div class="orbit orbit-one"></div>
            <div class="orbit orbit-two"></div>
            <div class="spark spark-one">✦</div>
            <div class="spark spark-two">✦</div>
            <div class="art-card card-dark"><span>48</span><small>hours to<br />make it real</small></div>
            <div class="art-card card-lime">IDEA<br />→<br />IMPACT</div>
            <div class="sticker">NO<br />BAD<br />IDEAS</div>
          </div>
        </div>

        <div class="ticker" aria-label="Event themes">
          <span>CREATE</span><b>✦</b><span>COLLABORATE</span><b>✦</b><span>CHALLENGE</span><b>✦</b><span>SHIP</span>
        </div>

        <div class="steps">
          <article><span>01</span><h3>Pick a problem</h3><p>Choose something real, specific, and worth improving.</p></article>
          <article><span>02</span><h3>Find your people</h3><p>Mix skills and perspectives. Small teams move quickly.</p></article>
          <article><span>03</span><h3>Show the work</h3><p>Make a useful prototype, then tell us what you learned.</p></article>
        </div>
      </section>

      <section v-else-if="activeTab === 'Jobs'" class="page inner-page">
        <div class="page-heading">
          <div><div class="eyebrow"><span></span> Open team roles</div><h1>Find your<br /><em>people.</em></h1></div>
          <p>Great ideas need mixed perspectives. Browse the sample openings below and imagine where you could contribute.</p>
        </div>

        <div class="job-list">
          <article v-for="job in jobs" :key="job.title" class="job-card">
            <div class="job-icon" :class="job.color">{{ job.icon }}</div>
            <div class="job-main"><span class="team">{{ job.team }}</span><h2>{{ job.title }}</h2><p>{{ job.detail }}</p></div>
            <div class="tags"><span v-for="tag in job.tags" :key="tag">{{ tag }}</span></div>
            <button aria-label="View role details">↗</button>
          </article>
        </div>

        <div class="note-bar"><span>Don’t see your role?</span> Every skill has a place at the table. Bring what you know — and what you want to learn.</div>
      </section>

      <PathPage v-else />
    </main>

    <footer><span>HackShift / Demo showcase</span><span>Made for curious builders ✦</span></footer>
  </div>
</template>
