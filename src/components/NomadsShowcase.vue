<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">十二星座运势与塔罗专家实战模板库</h2>
        <p class="showcase-subtitle">精选典型场景与实战模版，点击“一键套用”快速体验</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个实战模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次生成</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const emit = defineEmits<{
  (e: 'apply-template', payload: { prompt: string }): void;
}>();

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  usageCount: string;
}

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'ai-xingzuo-1',
    tag: '水逆避坑',
    title: '水星逆行期间十二星座防踩雷运势',
    prompt: '分析水逆对十二星座沟通与电子设备的影响，提供各星座情绪安适指南。',
    usageCount: '58.2k'
  },
  {
    id: 'ai-xingzuo-2',
    tag: '塔罗占卜',
    title: '塔罗三张牌阵：过去的羁绊与未来趋势',
    prompt: '基于“圣杯七、隐士、太阳”三张牌，解读感情发展趋势并给予理性建议。',
    usageCount: '52.4k'
  },
  {
    id: 'ai-xingzuo-3',
    tag: '星座合盘',
    title: '处女座与巨蟹座：理性与感性的完美互补',
    prompt: '深度剖析处女座与巨蟹座的情感合盘，分析性格契合点与摩擦化解秘诀。',
    usageCount: '46.1k'
  },
  {
    id: 'ai-xingzuo-4',
    tag: '事业财运',
    title: '摩羯座事业瓶颈突破与下半年财运',
    prompt: '分析摩羯座星盘相位，提供事业突破口、跳槽时机及理财避坑建议。',
    usageCount: '40.8k'
  },
  {
    id: 'ai-xingzuo-5',
    tag: '脱单建议',
    title: '风象星座（双子/天秤/水瓶）脱单指南',
    prompt: '为风象星座提供社交破冰策略，分析吸引正缘桃花的开运风格与场所。',
    usageCount: '35.1k'
  },
  {
    id: 'ai-xingzuo-6',
    tag: '心理疗愈',
    title: '缓解焦虑的星座心理疗愈与正念金句',
    prompt: '根据十二星座性格弱点，提供 12 句触动心灵的治愈金句与正念练习。',
    usageCount: '30.6k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>
