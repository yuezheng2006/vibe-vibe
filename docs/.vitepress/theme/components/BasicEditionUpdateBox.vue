<template>
  <div class="basic-edition-update-box">
    <div class="basic-edition-update-box__header">
      <span class="basic-edition-update-box__badge">{{ copy.badge }}</span>
      <h3>{{ copy.title }}</h3>
    </div>

    <p class="basic-edition-update-box__intro">
      {{ copy.intro }}
    </p>

    <div class="basic-edition-update-box__grid">
      <section class="basic-edition-update-box__card">
        <h4>{{ copy.positioningTitle }}</h4>
        <p v-html="copy.positioningBody"></p>
      </section>

      <section class="basic-edition-update-box__card">
        <h4>{{ copy.advantageTitle }}</h4>
        <p>{{ copy.advantageBody }}</p>
      </section>

      <section class="basic-edition-update-box__card">
        <h4>{{ copy.goalTitle }}</h4>
        <p v-html="copy.goalBody"></p>
      </section>
    </div>

    <div class="basic-edition-update-box__footer">
      <strong>{{ copy.footerLead }}</strong>
      {{ copy.footerBody }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { useRoute } from 'vitepress'

const route = useRoute()

const zhCopy = {
  badge: '新版说明',
  title: '这一版基础篇和旧版有什么不同？',
  intro:
    '如果你学过旧版，或者正在学旧版，这里先给你一个最快判断：新版不是在旧版上零碎加几段补丁，而是把整套基础篇重排成了一条更连续、更适合独立 vibe coder 的主线。',
  positioningTitle: '立意',
  positioningBody:
    '新版把全篇收束到一个连续案例：<strong>个人主页 + 数字分身</strong>。不再让读者在很多零散例子和概念之间来回跳，而是围绕同一个作品，走完从想法到上线的第一次完整闭环。',
  advantageTitle: '优势',
  advantageBody:
    '新版更强调“先做出来，再逐步理解”。章节顺序更贴近真实 AI 协作流程：先生成第一版，再带回本地、改界面、补内容、调数字分身、最后上线。新手高频卡点也被更明确地放进正文和附录里了。',
  goalTitle: '目标',
  goalBody:
    '新版的目标不是把你一次培养成专业工程师，而是帮你建立三种最关键的基本能力：<strong>做得出来、改得动、能上线</strong>。当你真正做完第一个作品，后面的技术学习才更容易有抓手。',
  footerLead: '如果你学过旧版：',
  footerBody:
    '可以直接把当前基础篇当成主线版本来读，不需要来回对照旧版。要是你已经做到一半，也可以直接切到新版对应阶段：已经做出原型，就从第 2 章接上；已经在改页面，就从第 3 章往后继续。'
}

const enCopy = {
  badge: 'Edition Note',
  title: 'How is this Fundamentals edition different from the old one?',
  intro:
    'If you have studied the old edition, or are still reading it, here is the fastest way to understand the change: the new edition is not just a few patchy updates. It has been reorganized into one clearer mainline storyline.',
  positioningTitle: 'Positioning',
  positioningBody:
    'The new edition is built around one continuous case: <strong>a personal homepage + digital twin</strong>. Instead of jumping back and forth between scattered examples and concepts, you follow one project all the way through your first full loop from idea to launch.',
  advantageTitle: 'Strength',
  advantageBody:
    'The new edition emphasizes building first, then understanding step by step. The chapter order follows a more realistic AI collaboration flow: generate the first version, bring it local, improve the interface, complete the content, tune the digital twin, and launch it.',
  goalTitle: 'Goal',
  goalBody:
    'The goal is not to turn you into a professional engineer overnight. It is to help you build three core abilities: <strong>make it real, keep changing it, and ship it</strong>. Once you finish your first real project, later technical learning becomes much easier to anchor.',
  footerLead: 'If you used the old edition:',
  footerBody:
    'you can treat the current Fundamentals as the mainline version and read it directly without cross-checking the old one. If you already have a prototype, jump in from Chapter 2. If you are already refining the page, continue from Chapter 3 onward.'
}

const copy = computed(() => (route.path.startsWith('/en') ? enCopy : zhCopy))
</script>

<style scoped>
.basic-edition-update-box {
  margin: 20px 0 28px;
  padding: 20px;
  border: 1px solid color-mix(in srgb, var(--vp-c-brand-1) 18%, var(--vp-c-divider));
  border-radius: 18px;
  background:
    radial-gradient(circle at top right, color-mix(in srgb, var(--vp-c-brand-1) 12%, transparent), transparent 38%),
    linear-gradient(180deg, var(--vp-c-bg-soft), var(--vp-c-bg-elv));
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.04);
}

.basic-edition-update-box__header {
  margin-bottom: 12px;
}

.basic-edition-update-box__badge {
  display: inline-flex;
  align-items: center;
  padding: 4px 10px;
  border-radius: 999px;
  background: color-mix(in srgb, var(--vp-c-brand-1) 12%, var(--vp-c-bg));
  color: var(--vp-c-brand-1);
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 0.04em;
}

.basic-edition-update-box__header h3 {
  margin: 10px 0 0;
  font-size: 22px;
  line-height: 1.3;
}

.basic-edition-update-box__intro {
  margin: 0 0 16px;
  color: var(--vp-c-text-2);
  line-height: 1.75;
}

.basic-edition-update-box__grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 12px;
  margin-bottom: 16px;
}

.basic-edition-update-box__card {
  padding: 14px 14px 12px;
  border: 1px solid var(--vp-c-divider);
  border-radius: 14px;
  background: color-mix(in srgb, var(--vp-c-bg) 78%, var(--vp-c-brand-1) 4%);
}

.basic-edition-update-box__card h4 {
  margin: 0 0 8px;
  font-size: 15px;
}

.basic-edition-update-box__card p,
.basic-edition-update-box__footer {
  margin: 0;
  color: var(--vp-c-text-2);
  line-height: 1.75;
  font-size: 14px;
}

.basic-edition-update-box__footer {
  padding-top: 14px;
  border-top: 1px dashed var(--vp-c-divider);
}

.basic-edition-update-box strong {
  color: var(--vp-c-text-1);
}

@media (max-width: 860px) {
  .basic-edition-update-box__grid {
    grid-template-columns: 1fr;
  }
}
</style>
