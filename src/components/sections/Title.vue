<script lang="ts" setup>

import { ElIcon } from 'element-plus'
import { Document, Files, MagicStick, Film, Link as LinkIcon } from '@element-plus/icons-vue'

// Badge
const badge = 'Technical Report'

// 标题
const title = 'Academic Project Page Template'

// 副标题
const subtitle = 'A modern dark-themed project page for research papers'

// 作者清单
const authors = [
  { name: "Author One", homepage: "#", flags: "1,*" },
  { name: "Author Two", homepage: "#", flags: "2" },
  { name: "Author Three", homepage: "#", flags: "1" },
]

// 单位清单
const affiliations = [
  { flag: "1", name: "University A" },
  { flag: "2", name: "University B" },
]

// 脚注
const footnote = "* Corresponding Author"

// 按钮
const buttons = [
  { name: "Paper", href: "#", icon: Document },
  { name: "arXiv", href: "#", icon: Document },
  { name: "Code", href: "https://github.com/JunyaoHu/academic-project-page-template-vue", icon: Files },
  { name: "Demo", href: "#", icon: MagicStick },
  { name: "Video", href: "#", icon: Film },
  { name: "BibTeX", href: "#bibtex", icon: LinkIcon },
]

// 统计数字
const stats = [
  { value: '12', label: 'Tasks' },
  { value: '5', label: 'Benchmarks' },
  { value: '100K+', label: 'Trajectories' },
  { value: '50+', label: 'Scenes' },
]

</script>

<template>
  <section id="overview" class="hero">
    <div class="hero-inner">

      <!-- Badge -->
      <div class="hero-badge">{{ badge }}</div>

      <!-- Title -->
      <h1 class="hero-title">{{ title }}</h1>

      <!-- Subtitle -->
      <p class="hero-subtitle">{{ subtitle }}</p>

      <!-- Authors -->
      <div class="hero-authors">
        <template v-for="(author, idx) in authors" :key="author.name">
          <a :href="author.homepage" class="author-link">
            {{ author.name }}<sup v-if="author.flags">{{ author.flags }}</sup>
          </a>
          <span v-if="idx < authors.length - 1" class="author-sep">,&nbsp;</span>
        </template>
      </div>

      <!-- Affiliations -->
      <div class="hero-affiliations">
        <template v-for="(aff, idx) in affiliations" :key="aff.flag">
          <span class="affiliation">
            <sup>{{ aff.flag }}</sup>{{ aff.name }}
          </span>
          <span v-if="idx < affiliations.length - 1" class="aff-sep">&nbsp;&nbsp;</span>
        </template>
      </div>

      <!-- Footnote -->
      <div class="hero-footnote">{{ footnote }}</div>

      <!-- Buttons -->
      <div class="hero-buttons">
        <a v-for="btn in buttons" :key="btn.name" :href="btn.href" class="hero-btn">
          <el-icon :size="16"><component :is="btn.icon" /></el-icon>
          <span>{{ btn.name }}</span>
        </a>
      </div>

      <!-- Stats -->
      <div class="hero-stats">
        <div v-for="stat in stats" :key="stat.label" class="stat-card">
          <div class="stat-value">{{ stat.value }}</div>
          <div class="stat-label">{{ stat.label }}</div>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.hero {
  padding: 100px 24px 48px;
  text-align: center;
}

.hero-inner {
  max-width: var(--content-max-width);
  margin: 0 auto;
}

/* Badge */
.hero-badge {
  display: inline-block;
  padding: 4px 14px;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: var(--accent);
  border: 1px solid var(--accent);
  border-radius: 20px;
  margin-bottom: 24px;
}

/* Title — gradient art text */
.hero-title {
  font-family: "MyFont", -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  font-size: 64px;
  font-weight: 700;
  line-height: 1.15;
  margin: 0 0 16px;
  letter-spacing: 1px;
  background: linear-gradient(135deg, #CF7359 0%, #CF7359 70%, #ffffff 100%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

/* Subtitle */
.hero-subtitle {
  font-size: 18px;
  color: var(--text-secondary);
  margin: 0 0 32px;
  line-height: 1.6;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

/* Authors */
.hero-authors {
  margin-bottom: 8px;
  font-size: 17px;
  line-height: 1.8;
}

.author-link {
  color: var(--text-primary);
  text-decoration: none;
  transition: color var(--transition-fast);
}
.author-link:hover {
  color: var(--accent);
}
.author-link sup {
  color: var(--text-tertiary);
  margin-left: 1px;
  font-size: 11px;
}

.author-sep {
  color: var(--text-tertiary);
}

/* Affiliations */
.hero-affiliations {
  margin-bottom: 6px;
  font-size: 15px;
  color: var(--text-secondary);
}
.affiliation sup {
  color: var(--text-tertiary);
  margin-right: 2px;
  font-size: 11px;
}

/* Footnote */
.hero-footnote {
  font-size: 13px;
  color: var(--text-tertiary);
  margin-bottom: 32px;
}

/* Buttons */
.hero-buttons {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
  margin-bottom: 48px;
}

.hero-btn {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 8px 18px;
  font-size: 14px;
  font-weight: 500;
  color: var(--text-primary);
  background: var(--bg-card);
  border: 1px solid var(--border-subtle);
  border-radius: 8px;
  text-decoration: none;
  transition: all var(--transition-fast);
}
.hero-btn:hover {
  background: var(--bg-card-hover);
  border-color: var(--accent);
  color: var(--accent);
}

/* Stats */
.hero-stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
  max-width: 700px;
  margin: 0 auto;
}

.stat-card {
  background: var(--bg-card);
  border: 1px solid var(--border-card);
  border-radius: var(--radius-md);
  padding: 20px 12px;
  text-align: center;
}

.stat-value {
  font-size: 28px;
  font-weight: 700;
  color: var(--accent);
  margin-bottom: 4px;
}

.stat-label {
  font-size: 13px;
  color: var(--text-secondary);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

/* Responsive */
@media (max-width: 768px) {
  .hero {
    padding: 80px 16px 32px;
  }
  .hero-title {
    font-size: 32px;
  }
  .hero-subtitle {
    font-size: 15px;
  }
  .hero-authors {
    font-size: 15px;
  }
  .hero-stats {
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
  }
  .stat-value {
    font-size: 22px;
  }
  .hero-btn {
    padding: 7px 14px;
    font-size: 13px;
  }
}
</style>
