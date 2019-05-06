<template lang="pug">
  div
    // skill
    skill(:img-src="git"
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
  import git from '~/assets/images/git.png';
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
        git,
        maxPoint: 6,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "テスト",
        skillMainDesc: "テストスキル。",
        skillDesc: "アプリケーション開発時のテストの手法を理解している。",
        skillPointText: {
          1: "Unit, Integration, Functionalテストのうち１つを理解し、実践している",
          2: "Unit, Integration, Functionalテストのうち２つを理解し、実践している",
          3: "Unit, Integration, Functionalテストのうちすべてを理解し、実践している",
          4: "Jest, Enzyme, Cypressのうち１つを理解し、使いこなせる",
          5: "Jest, Enzyme, Cypressのうち２つを理解し、使いこなせる",
          6: "Jest, Enzyme, Cypressのうちすべてを理解し、使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontTesting', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontTesting', this.currentPoint);
    }
  }
</script>
