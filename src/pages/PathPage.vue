<script setup>
const careers = [
  { number: '01', title: 'Product Designer', percent: 30, color: 'coral', detail: 'Turn ideas into useful, human experiences.' },
  { number: '02', title: 'Data Analyst', percent: 40, color: 'blue', detail: 'Find patterns and make evidence visible.' },
  { number: '03', title: 'Software Developer', percent: 50, color: 'lime', detail: 'Build the systems that bring ideas to life.' },
]
</script>

<template>
  <section class="page inner-page path-page">
    <div class="page-heading">
      <div><div class="eyebrow"><span></span> Career possibilities</div><h1>Where could<br /><em>you go?</em></h1></div>
      <p>Every journey begins at one point, then opens into different possibilities. Explore three potential career directions below.</p>
    </div>

    <div class="career-chart" aria-label="One person branching into three possible careers">
      <div class="start-column">
        <div class="person-node">
          <div class="person-icon" aria-hidden="true"><span></span></div>
          <div><small>STARTING POINT</small><strong>You</strong><p>Your skills, interests<br />and ambitions</p></div>
        </div>
        <div class="start-line" aria-hidden="true"><span></span></div>
      </div>

      <div class="career-paths">
        <article v-for="career in careers" :key="career.title" class="career-node" :class="career.color">
          <div class="path-line" aria-hidden="true"></div>
          <span class="career-number">{{ career.number }}</span>
          <div class="career-copy"><small>POSSIBLE CAREER</small><h2>{{ career.title }}</h2><p>{{ career.detail }}</p></div>
          <div class="career-score"><strong>{{ career.percent }}%</strong><span>possibility</span></div>
          <div class="probability-track" aria-hidden="true"><span :style="{ width: career.percent + '%' }"></span></div>
        </article>
      </div>
    </div>

    <p class="chart-note"><span>✦</span> These possibilities are independent indicators, so they do not need to add up to 100%.</p>
  </section>
</template>

<style scoped>
.career-chart { display: grid; grid-template-columns: .78fr 1.5fr; align-items: center; min-height: 500px; padding: 46px; border: 1px solid #aaa59c; background: rgba(255,255,255,.2); }
.start-column { display: grid; grid-template-columns: 1fr 90px; align-items: center; height: 100%; }
.person-node { display: flex; align-items: center; gap: 22px; padding: 28px; background: #151515; color: white; box-shadow: 8px 8px 0 #ff796d; }
.person-icon { flex: 0 0 auto; width: 72px; height: 72px; border-radius: 50%; background: #d9ff55; position: relative; overflow: hidden; }
.person-icon::before { content: ''; width: 22px; height: 22px; border-radius: 50%; background: #151515; position: absolute; left: 25px; top: 15px; }
.person-icon span { width: 44px; height: 30px; border-radius: 50% 50% 0 0; background: #151515; position: absolute; left: 14px; bottom: 0; }
.person-node small, .career-copy small { display: block; font-size: 10px; letter-spacing: .15em; font-weight: 800; color: #aaa59c; }
.person-node strong { display: block; font-family: 'Syne'; font-size: 34px; margin: 5px 0; }.person-node p { margin: 0; color: #c9c4b9; line-height: 1.4; font-size: 13px; }
.start-line { height: 72%; border-right: 2px solid #151515; position: relative; }.start-line::before { content: ''; position: absolute; left: 0; right: -1px; top: 50%; border-top: 2px solid #151515; }.start-line span::before, .start-line span::after { content: ''; position: absolute; right: -5px; width: 9px; height: 9px; border-radius: 50%; background: #151515; }.start-line span::before { top: 0; }.start-line span::after { bottom: 0; }
.career-paths { display: grid; gap: 18px; }
.career-node { min-height: 128px; display: grid; grid-template-columns: 26px 1fr auto; grid-template-rows: 1fr 8px; gap: 0 22px; align-items: center; padding: 20px 24px 0 0; position: relative; border: 1px solid #151515; }
.career-node.coral { background: #ff9b91; }.career-node.blue { background: #8ab0ff; }.career-node.lime { background: #d9ff55; }
.path-line { position: absolute; left: -91px; width: 91px; top: 50%; border-top: 2px solid #151515; }.path-line::after { content: ''; position: absolute; right: -1px; top: -5px; width: 9px; height: 9px; border-radius: 50%; background: #151515; }
.career-number { grid-row: 1; font-weight: 800; font-size: 12px; align-self: start; padding-top: 6px; }.career-copy { grid-row: 1; }.career-copy small { color: rgba(21,21,21,.55); }.career-copy h2 { font-family: 'Syne'; font-size: 25px; margin: 4px 0; }.career-copy p { margin: 0; color: rgba(21,21,21,.72); font-size: 13px; }
.career-score { grid-row: 1; display: flex; flex-direction: column; text-align: right; }.career-score strong { font-family: 'Syne'; font-size: 42px; line-height: 1; }.career-score span { font-size: 11px; text-transform: uppercase; letter-spacing: .12em; font-weight: 700; margin-top: 4px; }
.probability-track { grid-column: 1 / -1; grid-row: 2; height: 8px; background: rgba(21,21,21,.16); }.probability-track span { display: block; height: 100%; background: #151515; }
.chart-note { margin: 20px 0 0; color: #625f59; font-size: 13px; }.chart-note span { color: #ff6f61; margin-right: 7px; }
@media (max-width: 800px) { .career-chart { grid-template-columns: 1fr; padding: 24px 18px; gap: 58px; }.start-column { display: block; }.person-node { max-width: 310px; margin: 0 auto; }.start-line { width: 50%; height: 58px; margin: 0; border-right: 2px solid #151515; border-bottom: 2px solid #151515; }.start-line::before, .start-line span::before, .start-line span::after { display: none; }.career-paths { gap: 14px; }.career-node { grid-template-columns: 22px 1fr auto; padding-right: 15px; gap: 0 10px; }.path-line { display: none; }.career-copy h2 { font-size: 19px; }.career-copy p { display: none; }.career-score strong { font-size: 30px; } }
</style>
