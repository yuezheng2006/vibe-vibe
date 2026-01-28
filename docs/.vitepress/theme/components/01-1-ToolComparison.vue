<script setup lang="ts">
import { ref } from 'vue'

const tools = [
  {
    id: 'cli',
    name: 'CLI 工具',
    icon: '⌨️',
    examples: 'Vim, Git CLI, npm',
    pros: ['轻量快速', '远程友好', '可脚本化'],
    cons: ['学习曲线陡', '无图形界面'],
    bestFor: '服务器操作、自动化脚本'
  },
  {
    id: 'ide',
    name: 'IDE',
    icon: '🖥️',
    examples: 'VS Code, WebStorm',
    pros: ['功能丰富', '可视化调试', '插件生态'],
    cons: ['资源占用高', '启动较慢'],
    bestFor: '日常开发、大型项目'
  }
]

const selectedTool = ref<string | null>(null)
</script>

<template>
  <div class="tool-comparison">
    <div class="tools-grid">
      <div
        v-for="tool in tools"
        :key="tool.id"
        class="tool-card"
        :class="{ selected: selectedTool === tool.id }"
        @click="selectedTool = selectedTool === tool.id ? null : tool.id"
      >
        <div class="tool-header">
          <span class="tool-icon">{{ tool.icon }}</span>
          <span class="tool-name">{{ tool.name }}</span>
        </div>
        <div class="tool-examples">{{ tool.examples }}</div>

        <div class="tool-sections">
          <div class="section pros">
            <div class="section-title">✅ 优势</div>
            <ul>
              <li v-for="pro in tool.pros" :key="pro">{{ pro }}</li>
            </ul>
          </div>
          <div class="section cons">
            <div class="section-title">⚠️ 局限</div>
            <ul>
              <li v-for="con in tool.cons" :key="con">{{ con }}</li>
            </ul>
          </div>
        </div>

        <div class="best-for">
          <span class="label">适合场景：</span>
          <span class="value">{{ tool.bestFor }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.tool-comparison {
  background: linear-gradient(180deg, #f5f5f7 0%, #e8e8ed 100%);
  border-radius: 20px;
  padding: 24px;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.tools-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
}

.tool-card {
  background: white;
  border-radius: 16px;
  padding: 20px;
  cursor: pointer;
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.tool-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
}

.tool-card.selected {
  border-color: #007aff;
  box-shadow: 0 0 0 4px rgba(0, 122, 255, 0.1);
}

.tool-header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 8px;
}

.tool-icon {
  font-size: 28px;
}

.tool-name {
  font-size: 18px;
  font-weight: 600;
  color: #1d1d1f;
}

.tool-examples {
  font-size: 12px;
  color: #8e8e93;
  margin-bottom: 16px;
}

.tool-sections {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 16px;
}

.section {
  padding: 12px;
  border-radius: 10px;
}

.section.pros {
  background: rgba(52, 199, 89, 0.08);
}

.section.cons {
  background: rgba(255, 149, 0, 0.08);
}

.section-title {
  font-size: 12px;
  font-weight: 600;
  margin-bottom: 8px;
}

.section.pros .section-title {
  color: #34c759;
}

.section.cons .section-title {
  color: #ff9500;
}

.section ul {
  margin: 0;
  padding-left: 16px;
  font-size: 13px;
  color: #3a3a3c;
}

.section li {
  margin-bottom: 4px;
}

.best-for {
  padding-top: 12px;
  border-top: 1px solid #f5f5f7;
  font-size: 13px;
}

.best-for .label {
  color: #8e8e93;
}

.best-for .value {
  color: #007aff;
  font-weight: 500;
}

@media (max-width: 640px) {
  .tools-grid {
    grid-template-columns: 1fr;
  }
}
</style>
