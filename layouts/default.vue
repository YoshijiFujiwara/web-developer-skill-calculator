<template lang="pug">
  v-app
    // 上のナビゲーションバー
    v-toolbar
      v-toolbar-side-icon
      v-toolbar-title Title
      v-spacer
      v-toolbar-items.hidden-sm-and-down
        v-btn(flat='') 俺
        v-btn(flat='')
          nuxt-link(to="/skilltree") スキルツリー
        v-btn(flat='') 作品集

    // 中のコンテンツ
    v-content
      v-container(fluid)
        nuxt
</template>

<script>
  export default {
    data() {
      return {

      }
    }
  }
</script>
