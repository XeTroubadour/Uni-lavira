<script setup>
import page from '../mds/md.mdx';
import SectionWrapper from '../SectionWrapper.vue';
</script>

<template>
  <SectionWrapper id="method" title="Method">
    <div class="md-content">
      <page />
    </div>
  </SectionWrapper>
</template>

<style scoped>
.md-content {
  color: var(--text-primary);
  line-height: 1.8;
}
</style>
