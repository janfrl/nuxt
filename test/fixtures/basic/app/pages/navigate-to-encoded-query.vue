<template>
  <div>You should not see me</div>
</template>

<script setup lang="ts">
definePageMeta({
  middleware: (to) => {
    const targets: Record<string, string> = {
      slash: '/?callback=%2Fother',
      colon: '/?time=10%3A30',
      space: '/?q=hello%20world',
      plus: '/?q=hello+world',
      double: '/?callback=%252Fother',
      unicode: '/?q=%C3%B1',
      rawUnicode: '/?q=ñ',
      malformed: '/?q=%',
      hash: '/?q=%2F#frag%20x',
    }
    const target = typeof to.query.case === 'string' ? targets[to.query.case] : undefined
    return navigateTo(target || targets.slash)
  },
})
</script>
