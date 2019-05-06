<template lang="pug">
  div
    // skill
    skill(:img-src="solidkiss"
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
  import solidkiss from '~/assets/images/kiss.png';
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
        solidkiss,
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "SOLID, KISS, YAGNI",
        skillMainDesc: "プログラミングの原則的スキル。",
        skillDesc: "プログラミングの常識的な原則を抑えた上で、保守性の高いコーディングをすることができる。",
        skillPointText: {
          1: "SOLID, KISS, YAGNIのうち１つをよく知っている",
          2: "SOLID, KISS, YAGNIのうち２つをよく知っている",
          3: "SOLID, KISS, YAGNIすべてをよく知っている",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'baseSolid', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'baseSolid', this.currentPoint);
    }
  }
</script>
