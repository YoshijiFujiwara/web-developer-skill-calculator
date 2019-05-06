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
  import img from '~/assets/images/architecture.png';
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
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "CSSアーキテクチャ",
        skillMainDesc: "CSSアーキテクチャ。",
        skillDesc: "CSSアーキテクチャを理解し、保守性の高いコードの書き方ができる。",
        skillPointText: {
          1: "BEM, OOCSS, SMACSSのうち１つを理解し実践している",
          2: "BEM, OOCSS, SMACSSのうち２つを理解し実践している",
          3: "BEM, OOCSS, SMACSSのすべてを理解し実践している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontArchitecture', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontArchitecture', this.currentPoint);
    }
  }
</script>
