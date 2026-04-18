<script setup>
import { ref } from 'vue'

const projectName = 'Project'

const navItems = [
  { label: 'Overview', href: '#overview' },
  { label: 'Abstract', href: '#abstract' },
  { label: 'Method', href: '#method' },
  { label: 'Results', href: '#results' },
  { label: 'Demo', href: '#demo' },
  { label: 'BibTeX', href: '#bibtex' },
]

const mobileOpen = ref(false)

function toggleMobile() {
  mobileOpen.value = !mobileOpen.value
}

function closeMobile() {
  mobileOpen.value = false
}
</script>

<template>
  <nav class="navbar">
    <div class="navbar-inner">
      <!-- Left: project name -->
      <a href="#" class="navbar-brand" @click="closeMobile">{{ projectName }}</a>

      <!-- Hamburger button for mobile -->
      <button class="hamburger" :class="{ open: mobileOpen }" @click="toggleMobile" aria-label="Toggle navigation">
        <span></span>
        <span></span>
        <span></span>
      </button>

      <!-- Right: nav links -->
      <div class="navbar-links" :class="{ 'navbar-links--open': mobileOpen }">
        <a
          v-for="item in navItems"
          :key="item.href"
          :href="item.href"
          class="nav-link"
          @click="closeMobile"
        >
          {{ item.label }}
        </a>
      </div>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: var(--bg-nav);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border-subtle);
  height: 56px;
}

.navbar-inner {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 100%;
  padding: 0 24px;
}

.navbar-brand {
  font-family: "MyFont", sans-serif;
  font-size: 18px;
  font-weight: 600;
  color: var(--text-heading);
  text-decoration: none;
  letter-spacing: 1px;
  flex-shrink: 0;
}
.navbar-brand:hover {
  color: var(--accent);
}

.navbar-links {
  display: flex;
  gap: 8px;
  align-items: center;
}

.nav-link {
  color: var(--text-secondary);
  text-decoration: none;
  font-size: 14px;
  padding: 6px 12px;
  border-radius: var(--radius-sm);
  transition: color var(--transition-fast), background var(--transition-fast);
}
.nav-link:hover {
  color: var(--text-heading);
  background: rgba(255, 255, 255, 0.05);
}

/* Hamburger */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
  z-index: 1001;
}
.hamburger span {
  display: block;
  width: 22px;
  height: 2px;
  background: var(--text-secondary);
  border-radius: 1px;
  transition: transform 0.25s ease, opacity 0.25s ease;
}
.hamburger.open span:nth-child(1) {
  transform: translateY(7px) rotate(45deg);
}
.hamburger.open span:nth-child(2) {
  opacity: 0;
}
.hamburger.open span:nth-child(3) {
  transform: translateY(-7px) rotate(-45deg);
}

@media (max-width: 768px) {
  .hamburger {
    display: flex;
  }

  .navbar-links {
    position: fixed;
    top: 56px;
    left: 0;
    right: 0;
    flex-direction: column;
    background: var(--bg-nav);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border-subtle);
    padding: 12px 24px;
    gap: 4px;
    transform: translateY(-100%);
    opacity: 0;
    pointer-events: none;
    transition: transform 0.3s ease, opacity 0.3s ease;
  }

  .navbar-links--open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: all;
  }

  .nav-link {
    padding: 10px 12px;
    font-size: 15px;
    width: 100%;
    box-sizing: border-box;
  }
}
</style>
