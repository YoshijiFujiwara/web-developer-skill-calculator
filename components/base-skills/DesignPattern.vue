<template lang="pug">
  div
    // skill
    skill(:img-src="designpattern"
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
  import designpattern from '~/assets/images/designpattern.png';
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
        designpattern,
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "デザインパターン",
        skillMainDesc: "設計パターン把握スキル。",
        skillDesc: "デザインパターンを把握し、大規模開発において効率的なプログラミングができる。",
        skillPointText: {
          1: "デザインパターンについて、聞いたことがある",
          2: "デザインパターンを意識して使ったことがある",
          3: "実際のプロジェクトでデザインパターンを使用したことがある",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'baseDesignPattern', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'baseDesignPattern', this.currentPoint);
    }
  }
</script>
