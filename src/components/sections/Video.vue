<script setup>
import { ref, computed } from 'vue'
import SectionWrapper from '../SectionWrapper.vue'

const rawBase = import.meta.env.BASE_URL
const base = rawBase.endsWith('/') ? rawBase : `${rawBase}/`

// --- Fixed videos ---
const fixedVideos = [
  `${base}video_compressed/01.mp4`,
  `${base}video_compressed/02.mp4`,
]

// --- Filterable demo data ---
const robots = [
  { label: 'Aloha', value: 'Aloha' },
  { label: 'UAV',   value: 'UAV' },
  { label: 'G1',    value: 'G1' },
  { label: 'GO1',   value: 'GO1' },
]

const tasks = [
  { label: 'VLN',       value: 'vln' },
  { label: 'ObjectNav', value: 'objnav' },
  { label: 'EQA',       value: 'eqa' },
]

const scenes = [
  { label: 'Indoor',  value: 'indoor' },
  { label: 'Hall',    value: 'hall' },
  { label: 'Outdoor', value: 'outdoor' },
]

const combos = [
  { idx: 1, scene: 'indoor',  task: 'vln',    target: 'TV' },
  { idx: 2, scene: 'indoor',  task: 'objnav', target: 'flower' },
  { idx: 3, scene: 'indoor',  task: 'eqa',    target: 'GreenChair' },
  { idx: 4, scene: 'hall',    task: 'vln',    target: 'vase' },
  { idx: 5, scene: 'hall',    task: 'eqa',    target: 'TrashBin' },
  { idx: 6, scene: 'hall',    task: 'objnav', target: 'bike' },
  { idx: 7, scene: 'outdoor', task: 'vln',    target: 'stool' },
  { idx: 8, scene: 'outdoor', task: 'objnav', target: 'bike' },
  { idx: 9, scene: 'outdoor', task: 'eqa',    target: 'sofa' },
]

const selectedRobot = ref('Aloha')
const selectedTask  = ref('vln')
const selectedScene = ref('indoor')

const matched = computed(() => {
  return combos.find(c => c.scene === selectedScene.value && c.task === selectedTask.value)
})

const currentSrc = computed(() => {
  if (!matched.value) return ''
  const r = selectedRobot.value
  const c = matched.value
  const filename = `${r}_${c.idx}_${c.scene}_${c.task}_${c.target}.mp4`
  return `${base}video_compressed/Edited/${r}/${filename}`
})

const currentLabel = computed(() => {
  if (!matched.value) return ''
  const robotLabel = robots.find(r => r.value === selectedRobot.value)?.label
  const sceneLabel = scenes.find(s => s.value === selectedScene.value)?.label
  const taskLabel  = tasks.find(t => t.value === selectedTask.value)?.label
  return `${robotLabel} · ${sceneLabel} · ${taskLabel} · ${matched.value.target}`
})
</script>

<template>
  <section id="demo" class="demo-section">

    <!-- Fixed videos: no title, no caption -->
    <div class="fixed-videos">
      <video
        v-for="(src, i) in fixedVideos"
        :key="i"
        :src="src"
        controls
        preload="metadata"
        playsinline
        class="demo-video"
      ></video>
    </div>

    <!-- Demo title + filter module -->
    <SectionWrapper title="Demo">

      <!-- Filters -->
      <div class="filter-group">
        <span class="filter-label">Robot</span>
        <div class="filter-pills">
          <button
            v-for="r in robots" :key="r.value"
            :class="['pill', { active: selectedRobot === r.value }]"
            @click="selectedRobot = r.value"
          >{{ r.label }}</button>
        </div>
      </div>

      <div class="filter-group">
        <span class="filter-label">Task</span>
        <div class="filter-pills">
          <button
            v-for="t in tasks" :key="t.value"
            :class="['pill', { active: selectedTask === t.value }]"
            @click="selectedTask = t.value"
          >{{ t.label }}</button>
        </div>
      </div>

      <div class="filter-group">
        <span class="filter-label">Scene</span>
        <div class="filter-pills">
          <button
            v-for="s in scenes" :key="s.value"
            :class="['pill', { active: selectedScene === s.value }]"
            @click="selectedScene = s.value"
          >{{ s.label }}</button>
        </div>
      </div>

      <!-- Matched video -->
      <div v-if="matched" style="margin-top: 24px;">
        <video
          :key="currentSrc"
          :src="currentSrc"
          controls
          preload="metadata"
          playsinline
          class="demo-video"
        ></video>
        <p class="video-caption">{{ currentLabel }}</p>
      </div>
      <div v-else class="no-match">
        <p>No matching video for this combination.</p>
      </div>

    </SectionWrapper>

  </section>
</template>

<style scoped>
.demo-section {
  width: 100%;
}

/* Fixed videos area */
.fixed-videos {
  display: flex;
  flex-direction: column;
  gap: 24px;
  max-width: var(--content-max-width);
  margin: 0 auto;
  padding: 0 24px;
}

/* Shared video style */
.demo-video {
  display: block;
  width: 100%;
  height: auto;
  border-radius: var(--radius-md);
  border: 1px solid var(--border-subtle);
  background: var(--bg-card);
}

/* Filters */
.filter-group {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
  flex-wrap: wrap;
}

.filter-label {
  font-size: 14px;
  font-weight: 600;
  color: var(--text-secondary);
  min-width: 52px;
  flex-shrink: 0;
}

.filter-pills {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.pill {
  padding: 6px 16px;
  font-size: 13px;
  font-weight: 500;
  color: var(--text-secondary);
  background: transparent;
  border: 1px solid var(--border-subtle);
  border-radius: 20px;
  cursor: pointer;
  transition: all var(--transition-fast);
}
.pill:hover {
  color: var(--text-primary);
  border-color: var(--accent);
}
.pill.active {
  color: #fff;
  background: var(--accent);
  border-color: var(--accent);
}

.video-caption {
  text-align: center;
  font-size: 14px;
  color: var(--text-secondary);
  margin: 12px 0 0;
}

.no-match {
  text-align: center;
  padding: 40px 0;
  color: var(--text-tertiary);
}

@media (max-width: 768px) {
  .fixed-videos {
    padding: 0 16px;
  }
}
</style>
