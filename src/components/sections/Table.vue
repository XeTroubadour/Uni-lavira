<script lang="ts" setup>
import SectionWrapper from '../SectionWrapper.vue';

const tableData = [
  { model: 'Model A', params: '10 B', value_a: '123', value_b: '321' },
  { model: 'Model B', params: '30 B', value_a: '456', value_b: '654' },
  { model: 'Model C', params: '20 B', value_a: '789', value_b: '987' },
  { model: 'Model D', params: '5 B', value_a: '100', value_b: '200' },
]
</script>

<template>
  <SectionWrapper id="results" title="Results">
    <div class="table-card">
      <el-tabs class="dark-tabs" model-value="Method A">
        <el-tab-pane label="Method A" name="Method A">
          <el-table :data="tableData" :default-sort="{ prop: 'value_b', order: 'descending' }" scrollbar-always-on>
            <el-table-column prop="model" label="Model" width="100" sortable/>
            <el-table-column prop="params" label="#Params" min-width="120" sortable/>
            <el-table-column prop="value_a" label="Value A" min-width="120" sortable/>
            <el-table-column prop="value_b" label="Value B" min-width="120" sortable/>
          </el-table>
        </el-tab-pane>
        <el-tab-pane label="Method B" name="Method B">
          <p style="color: var(--text-secondary); padding: 20px;">Method B results placeholder</p>
        </el-tab-pane>
        <el-tab-pane label="Method C" name="Method C">
          <p style="color: var(--text-secondary); padding: 20px;">Method C results placeholder</p>
        </el-tab-pane>
      </el-tabs>
    </div>
  </SectionWrapper>
</template>

<style scoped>
.table-card {
  background: var(--bg-card);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-md);
  padding: 20px;
  overflow: hidden;
}

/* Tabs dark theme */
:deep(.el-tabs__nav-wrap::after) {
  background-color: var(--border-subtle) !important;
}
:deep(.el-tabs__item) {
  color: var(--text-secondary) !important;
}
:deep(.el-tabs__item.is-active) {
  color: var(--accent) !important;
}
:deep(.el-tabs__item:hover) {
  color: var(--text-primary) !important;
}
:deep(.el-tabs__active-bar) {
  background-color: var(--accent) !important;
}

/* Table dark theme */
:deep(.el-table) {
  --el-table-bg-color: transparent;
  --el-table-tr-bg-color: transparent;
  --el-table-header-bg-color: var(--bg-secondary);
  --el-table-row-hover-bg-color: var(--bg-card-hover);
  --el-table-border-color: var(--border-subtle);
  --el-table-text-color: var(--text-primary);
  --el-table-header-text-color: var(--text-heading);
  --el-table-current-row-bg-color: var(--bg-card-hover);
  color: var(--text-primary);
}
:deep(.el-table th.el-table__cell) {
  background-color: var(--bg-secondary) !important;
  color: var(--text-heading);
  border-bottom-color: var(--border-subtle);
}
:deep(.el-table td.el-table__cell) {
  border-bottom-color: var(--border-subtle);
}
:deep(.el-table--enable-row-hover .el-table__body tr:hover > td.el-table__cell) {
  background-color: var(--bg-card-hover) !important;
}
:deep(.el-table .sort-caret.ascending) {
  border-bottom-color: var(--text-tertiary);
}
:deep(.el-table .sort-caret.descending) {
  border-top-color: var(--text-tertiary);
}
:deep(.el-table .ascending .sort-caret.ascending) {
  border-bottom-color: var(--accent);
}
:deep(.el-table .descending .sort-caret.descending) {
  border-top-color: var(--accent);
}

/* Scrollbar */
:deep(.el-scrollbar__bar) {
  background-color: var(--text-tertiary);
}
:deep(.el-scrollbar__thumb) {
  background-color: var(--text-tertiary);
}
</style>
