<template>
  <div class="footer">
    <p class="footer-text">
      Built with <a href="https://cn.vuejs.org/">Vue</a> &amp; <a href="https://cn.vitejs.dev/">Vite</a>
    </p>
  </div>
</template>

<style scoped>
.footer {
  background-color: var(--bg-secondary);
  border-top: 1px solid var(--border-subtle);
  padding: 24px;
  text-align: center;
}

.footer-text {
  font-size: 13px;
  color: var(--text-tertiary);
  margin: 0;
}

.footer-text a {
  color: var(--text-secondary);
  text-decoration: none;
  transition: color var(--transition-fast);
}

.footer-text a:hover {
  color: var(--accent);
}
</style>
