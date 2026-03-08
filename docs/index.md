---
title: Vibe Vibe
titleTemplate: false
head:
  - - meta
    - http-equiv: refresh
      content: 0; url=/en/
---

<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  if (typeof window !== 'undefined' && window.location.pathname === '/') {
    window.location.replace('/en/')
  }
})
</script>

# Redirecting to English

English is now the default entry for Vibe Vibe.

- [Continue in English](/en/)
- [进入中文版本](/zh/)
