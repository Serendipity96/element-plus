<template>
  <div>
    <template v-for="(shadow, i) in shadowGroup" :key="i">
      <div
        class="demo-shadow"
        :style="{ boxShadow: `var(--el-box-shadow-${shadow.type})` }"
      />
      <span class="demo-shadow-text"
        >{{ shadow.name }}
        <code>box-shadow: {{ getValue(shadow.type) }}</code></span
      >
    </template>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'

const shadowGroup = ref([
  {
    name: 'Basic Shadow',
    type: 'base',
  },
  {
    name: 'Light Shadow',
    type: 'light',
  },
])
const getValue = (type: string) => {
  const getCssVarValue = (prefix, type) =>
    getComputedStyle(document.documentElement).getPropertyValue(
      `--el-${prefix}-${type}`
    )
  return getCssVarValue('box-shadow', type)
}
</script>
<style scoped>
.demo-shadow {
  height: 100px;
  width: 50%;
}
.demo-shadow-text {
  line-height: 50px;
  color: var(--el-text-color-regular);
  font-size: 14px;
}
</style>
