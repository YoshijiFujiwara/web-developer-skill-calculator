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
  import img from '~/assets/images/checklist.png';
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
        maxPoint: 1,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "実践的なテスト",
        skillMainDesc: "TestForPracticalStep。",
        skillDesc: "実践的なテストの仕方を心得ている。",
        skillPointText: {
          1: "実践的なテストの仕方を心得ている",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backTestForPracticalStep', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backTestForPracticalStep', this.currentPoint);
    }
  }
</script>
