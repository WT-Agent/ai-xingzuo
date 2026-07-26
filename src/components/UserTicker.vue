<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[生成完成]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  {
    "text": "用户 138****9911 完成了天蝎座水逆期间财运与避坑指南"
  },
  {
    "text": "用户 189****4422 得到了塔罗牌“恋人”与“命运之轮”感情解读"
  },
  {
    "text": "用户 131****7700 完成了狮子座与射手座合盘相处秘诀"
  },
  {
    "text": "用户 156****3355 生成了 2026 下半年风象星座事业转机分析"
  },
  {
    "text": "用户 173****8899 取得了专属幸运颜色与心灵疗愈引导语"
  }
]);
</script>
