<script>

import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Footer from './components/Footer.vue'

export default {
  components: {
    Header,
    Main,
    Footer,
  }
}

</script>

<template>
    <div class="app-root">

      <el-container>
        <el-header><Header/></el-header>
        <el-main><Main/></el-main>
        <el-footer><Footer/></el-footer>
      </el-container>

      <!-- 回到顶部 -->
      <el-backtop :right="40" :bottom="80" />
    </div>
</template>

<style>

/* ============================================
   Global Typography — Dark Theme
   ============================================ */

h1 {
  font-family: "MyFont", Verdana, sans-serif;
  letter-spacing: 2px;
  font-size: 28px;
  margin: 0px;
  text-align: center;
  color: var(--text-heading);
}

h2, h3, h4, h5, h6 {
  font-family: "MyFont", Verdana, sans-serif;
  letter-spacing: 2px;
  color: var(--text-heading);
}

.el-header {
  padding: 0px;
}

.el-footer {
  padding: 0px;
}

p, li {
  font-size: 16px;
  line-height: 1.75rem;
  color: var(--text-primary);
}

/* Code — dark */
code {
  font-family: 'Consolas', monospace;
  border-radius: 5px;
  padding: 2px 5px;
  background: var(--bg-code);
  color: var(--text-primary);
  border: 1px solid var(--border-subtle);
}

pre {
  border-radius: var(--radius-md);
  padding: 16px;
  background: var(--bg-code);
  line-height: 1.5rem;
  border: 1px solid var(--border-subtle);
}

pre:not(pre[id=bibtex]) {
  overflow-x: auto;
}

pre code {
  font-size: 14px;
  color: var(--text-primary);
  border: none;
  padding: 0px;
  background: transparent;
}

/* Blockquote — dark */
blockquote {
  border-left: 3px solid var(--accent);
  padding: 10px 20px;
  margin: 0px;
  background: var(--bg-card);
  border-radius: 0 var(--radius-sm) var(--radius-sm) 0;
}

blockquote > p {
  margin-block-start: 0.5em;
  margin-block-end: 0.5em;
  color: var(--text-secondary);
}

/* Links — accent */
a {
  color: var(--accent);
  text-decoration: none;
  transition: color var(--transition-fast);
}

a:hover {
  color: var(--accent-hover);
  border-bottom: none;
}

/* Images */
p > img {
  width: 80%;
  display: block;
  margin: 0 auto;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-card);
  border: 1px solid var(--border-subtle);
}

/* Tables — dark */
table {
  border-collapse: collapse;
  width: max-content;
  max-width: 100%;
  margin: 0 auto;
  display: block;
  overflow-x: auto;
  color: var(--text-primary);
}

thead {
  border-bottom-width: 1px;
  border-top-width: 2px;
  border-left-width: 0px;
  border-right-width: 0px;
  border-style: solid;
  border-color: var(--border-subtle);
}

tbody tr:last-child {
  border-bottom-width: 2px;
  border-top-width: 0px;
  border-left-width: 0px;
  border-right-width: 0px;
  border-style: solid;
  border-color: var(--border-subtle);
}

th {
  color: var(--text-heading);
}

th, td {
  padding-left: 1rem;
  padding-right: 1rem;
}

.katex-display {
  overflow-x: auto;
  overflow-y: hidden;
}

/* KaTeX dark text */
.katex {
  color: var(--text-primary);
}

</style>
