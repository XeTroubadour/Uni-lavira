<script setup>
import abstract from '../mds/abstract.mdx';
import SectionWrapper from '../SectionWrapper.vue';
</script>

<template>
  <SectionWrapper id="abstract" title="Abstract">
    <div class="abstract-content">
      <abstract />
    </div>
  </SectionWrapper>
</template>

<style scoped>
.abstract-content {
  font-size: 16px;
  line-height: 1.8;
  color: var(--text-primary);
  text-align: justify;
}
</style>
