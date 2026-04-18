<script setup>
import { ref } from 'vue'
import SectionWrapper from '../SectionWrapper.vue';

const bibtex = `@article{junyaohu2023template,
    title={Academic Project Page Template Vue},
    author={Hu, Junyao},
    journal={GitHub},
    year={2023}
}`

const copied = ref(false)

function copyBibtex() {
  navigator.clipboard.writeText(bibtex).then(() => {
    copied.value = true
    setTimeout(() => { copied.value = false }, 2000)
  })
}
</script>

<template>
  <SectionWrapper id="bibtex" title="BibTeX">
    <div class="bibtex-card">
      <div class="bibtex-header">
        <span class="bibtex-label">Citation</span>
        <button class="copy-btn" @click="copyBibtex">
          {{ copied ? 'Copied!' : 'Copy' }}
        </button>
      </div>
      <pre class="bibtex-code"><code>{{ bibtex }}</code></pre>
    </div>
  </SectionWrapper>
</template>

<style scoped>
.bibtex-card {
  background: var(--bg-code);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  overflow: hidden;
}

.bibtex-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 16px;
  border-bottom: 1px solid var(--border-subtle);
  background: var(--bg-card);
}

.bibtex-label {
  font-size: 13px;
  color: var(--text-secondary);
  font-weight: 500;
}

.copy-btn {
  padding: 4px 14px;
  font-size: 12px;
  font-weight: 500;
  color: var(--accent);
  background: transparent;
  border: 1px solid var(--accent);
  border-radius: var(--radius-sm);
  cursor: pointer;
  transition: all var(--transition-fast);
}
.copy-btn:hover {
  background: var(--accent-subtle);
}

.bibtex-code {
  margin: 0;
  padding: 16px 20px;
  background: transparent;
  border: none;
  border-radius: 0;
  overflow-x: auto;
}

.bibtex-code code {
  font-size: 14px;
  color: var(--text-primary);
  background: transparent;
  border: none;
  padding: 0;
  white-space: pre;
}
</style>
