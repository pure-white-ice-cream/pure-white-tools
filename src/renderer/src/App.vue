<script setup>
import { useDark, useToggle } from '@vueuse/core'
import { Sunny, Moon } from '@element-plus/icons-vue'

import Index from './page/Index.vue'
import Tool from './page/Tool.vue'
import About from './page/About.vue'

const isDark = useDark()
const toggleDark = useToggle(isDark)
</script>

<template>
  <el-tabs class="tabs">
    <el-tab-pane label="首页" class="index"> <Index /></el-tab-pane>
    <el-tab-pane label="工具箱"><Tool /></el-tab-pane>
    <el-tab-pane label="关于"><About /></el-tab-pane>
  </el-tabs>
  <el-button type="primary" plain class="dark-button" @click="toggleDark()">
    <text v-if="isDark">
      <el-icon><Sunny /></el-icon>
    </text>
    <text v-else>
      <el-icon><Moon /></el-icon>
    </text>
  </el-button>
</template>

<style lang="scss">
.tabs {
  width: 96%;
  margin: 0 auto;
}
.dark-button {
  position: absolute;
  right: 50px;
  top: 5px;
}
</style>
