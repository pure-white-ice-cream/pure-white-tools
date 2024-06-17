<script setup>
import { ref } from 'vue'
const progress = ref(false)
const percent = ref(0)
const checkOpen = () => {
  progress.value = true
  delayAndExecute()
}

async function delayAndExecute() {
  while (percent.value < 100) {
    await new Promise((resolve) => setTimeout(resolve, 10))
    if (percent.value == 89) {
      await new Promise((resolve) => setTimeout(resolve, 1000))
    }
    percent.value = percent.value + 1
  }
}
</script>
<template>
  <el-row justify="center">
    <el-button type="primary" plain @click="checkOpen">检查电脑开机状况</el-button>
  </el-row>
  <dev class="progress">
    <el-progress v-if="progress" :percentage="percent" striped striped-flow />
  </dev>
  <el-row justify="center">
    <text v-if="percent >= 100">恭喜！您的电脑正处于 【开机】 状态</text>
  </el-row>
</template>
<style lang="scss">
.progress {
  margin: 50px;
}
</style>
