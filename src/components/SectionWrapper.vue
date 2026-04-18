<script setup>
defineProps({
  id: { type: String, default: '' },
  title: { type: String, default: '' },
  wide: { type: Boolean, default: false },
})
</script>

<template>
  <section :id="id" class="section-wrapper">
    <div :class="['section-inner', { 'section-inner--wide': wide }]">
      <h2 v-if="title" class="section-title">{{ title }}</h2>
      <slot />
    </div>
  </section>
</template>

<style scoped>
.section-wrapper {
  padding: 48px 24px;
  width: 100%;
  box-sizing: border-box;
}

.section-inner {
  max-width: var(--content-max-width);
  margin: 0 auto;
}

.section-inner--wide {
  max-width: var(--content-wide-max-width);
}

.section-title {
  font-family: "MyFont", -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  font-size: 28px;
  font-weight: 600;
  color: var(--text-heading);
  letter-spacing: 1px;
  margin: 0 0 32px 0;
  text-align: center;
  position: relative;
}

.section-title::after {
  content: '';
  display: block;
  width: 40px;
  height: 2px;
  background: var(--accent);
  margin: 12px auto 0;
  border-radius: 1px;
}

@media (max-width: 768px) {
  .section-wrapper {
    padding: 32px 16px;
  }
  .section-title {
    font-size: 22px;
  }
}
</style>
