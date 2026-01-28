<script setup lang="ts">
import { ref, computed } from 'vue'

interface Layer {
  id: string
  name: string
  icon: string
  color: string
  items: string[]
  description: string
}

const layers: Layer[] = [
  {
    id: 'frontend',
    name: '前端层',
    icon: '🎨',
    color: '#007aff',
    items: ['HTML', 'CSS', 'JavaScript', 'React/Vue'],
    description: '用户直接看到的界面，运行在浏览器中'
  },
  {
    id: 'backend',
    name: '后端层',
    icon: '⚙️',
    color: '#5856d6',
    items: ['Node.js', 'Python', 'Java', 'Go'],
    description: '处理业务逻辑，运行在服务器上'
  },
  {
    id: 'database',
    name: '数据层',
    icon: '💾',
    color: '#34c759',
    items: ['PostgreSQL', 'MySQL', 'MongoDB', 'Redis'],
    description: '存储和管理数据'
  },
  {
    id: 'infra',
    name: '基础设施',
    icon: '🏗️',
    color: '#ff9500',
    items: ['服务器', 'Docker', 'Nginx', 'CDN'],
    description: '支撑应用运行的基础环境'
  }
]

const selectedLayer = ref<string | null>(null)

function selectLayer(id: string) {
  selectedLayer.value = selectedLayer.value === id ? null : id
}

const currentLayer = computed(() => layers.find(l => l.id === selectedLayer.value))
</script>

<template>
  <div class="tech-stack-layers">
    <div class="layers-container">
      <div
        v-for="(layer, index) in layers"
        :key="layer.id"
        class="layer-card"
        :class="{ selected: selectedLayer === layer.id, collapsed: selectedLayer && selectedLayer !== layer.id }"
        :style="{ '--layer-color': layer.color, zIndex: layers.length - index }"
        @click="selectLayer(layer.id)"
      >
        <div class="layer-header">
          <span class="layer-icon" :style="{ background: layer.color }">{{ layer.icon }}</span>
          <span class="layer-name">{{ layer.name }}</span>
          <span class="layer-number">{{ index + 1 }}</span>
        </div>

        <div class="layer-content">
          <div class="layer-items">
            <span v-for="item in layer.items" :key="item" class="item-tag">{{ item }}</span>
          </div>
          <p class="layer-desc">{{ layer.description }}</p>
        </div>
      </div>
    </div>

    <div v-if="currentLayer" class="layer-detail" :style="{ borderColor: currentLayer.color }">
      <h4 :style="{ color: currentLayer.color }">
        {{ currentLayer.icon }} {{ currentLayer.name }}
      </h4>
      <p>{{ currentLayer.description }}</p>
      <div class="detail-items">
        <div v-for="item in currentLayer.items" :key="item" class="detail-item">
          {{ item }}
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.tech-stack-layers {
  background: linear-gradient(180deg, #f5f5f7 0%, #e8e8ed 100%);
  border-radius: 20px;
  padding: 24px;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.layers-container {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.layer-card {
  background: white;
  border-radius: 16px;
  padding: 16px 20px;
  cursor: pointer;
  transition: all 0.3s ease;
  border: 2px solid transparent;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
}

.layer-card:hover {
  transform: translateX(8px);
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.08);
}

.layer-card.selected {
  border-color: var(--layer-color);
  box-shadow: 0 0 0 4px rgba(0, 0, 0, 0.04), 0 4px 20px rgba(0, 0, 0, 0.1);
}

.layer-card.collapsed {
  opacity: 0.6;
  transform: scale(0.98);
}

.layer-header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}

.layer-icon {
  width: 40px;
  height: 40px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
}

.layer-name {
  flex: 1;
  font-size: 17px;
  font-weight: 600;
  color: #1d1d1f;
}

.layer-number {
  width: 28px;
  height: 28px;
  border-radius: 50%;
  background: #f5f5f7;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  font-weight: 600;
  color: #8e8e93;
}

.layer-content {
  padding-left: 52px;
}

.layer-items {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 8px;
}

.item-tag {
  padding: 4px 10px;
  background: #f5f5f7;
  border-radius: 6px;
  font-size: 12px;
  color: #3a3a3c;
}

.layer-desc {
  font-size: 13px;
  color: #8e8e93;
  margin: 0;
}

.layer-detail {
  margin-top: 20px;
  padding: 20px;
  background: white;
  border-radius: 16px;
  border-left: 4px solid;
  animation: slideUp 0.3s ease;
}

@keyframes slideUp {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}

.layer-detail h4 {
  margin: 0 0 8px 0;
  font-size: 18px;
}

.layer-detail p {
  margin: 0 0 16px 0;
  font-size: 14px;
  color: #8e8e93;
}

.detail-items {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.detail-item {
  padding: 8px 16px;
  background: #f5f5f7;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 500;
}

@media (max-width: 640px) {
  .tech-stack-layers {
    padding: 16px;
  }

  .layer-content {
    padding-left: 0;
  }
}
</style>
