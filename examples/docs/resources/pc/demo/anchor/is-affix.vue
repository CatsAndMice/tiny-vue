<template>
  <div class="wrap">
    <tiny-anchor :links="links" is-affix></tiny-anchor>
  </div>
</template>

<script>
import { Anchor } from '@opentiny/vue'
export default {
  components: {
    TinyAnchor: Anchor
  },
  data() {
    return {
      links: [
        {
          key: 'demonstrate',
          link: '#demonstrate',
          title: '演示',
          children: [
            {
              key: 'basic-usage',
              link: '#basic-usage',
              title: 'Basic Usage'
            },
            {
              key: 'is-affix',
              link: '#is-affix',
              title: 'Is Affix'
            },
            {
              key: 'set-container',
              link: '#set-container',
              title: 'Set Container'
            },
            {
              key: 'on-change',
              link: '#on-change',
              title: 'On Change'
            }
          ]
        },
        {
          key: 'api',
          link: '#api',
          title: 'Api'
        }
      ]
    }
  }
}
</script>

<style scoped>
.wrap {
  height: 150px;
}
</style>
