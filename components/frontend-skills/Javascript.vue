<template lang="pug">
  div
    // skill
    skill(:img-src="img"
    :clickable="clickable"
    :max-point="maxPoint"
    :current-point="currentPoint"
    @mouseover.native="skillDescShow = true"
    @mouseleave.native="skillDescShow = false"
    @click.native="currentPoint = (clickable && currentPoint < maxPoint)? currentPoint + 1 : currentPoint")

    skill-card(v-if="skillDescShow"
    :skill-name="skillName"
    :skill-main-desc="skillMainDesc"
    :skill-desc="skillDesc"
    :current-point="currentPoint"
    :max-point="maxPoint"
    :skill-point-text="skillPointText")

</template>

<script>
  import img from '~/assets/images/javascript.png';
  import Skill from '~/components/Skill';
  import SkillCard from '~/components/SkillCard';


  export default {
    props: ["clickable"],
    components: {
      Skill,
      SkillCard
    },
    data() {
      return {
        img,
        maxPoint: 5,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "Javascript",
        skillMainDesc: "Javascriptスキル。",
        skillDesc: "フロントエンドに欠かせない、webページに動きをつけるスキル。",
        skillPointText: {
          1: "文法や、基本的な構成について理解している",
          2: "DOMの操作について理解している",
          3: "FetchAPI/Ajax(XHR)について理解している",
          4: "ES6、モジュールについて理解している",
          5: "Hosting?, イベントバブリング, スコープ, プロトタイプ, shadow DOM, strict, ブラウザの仕組み, DNS, HTTPの概念を理解している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontJavascript', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontJavascript', this.currentPoint);
    }
  }
</script>
