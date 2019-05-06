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
  import img from '~/assets/images/css-3.png';
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
        skillName: "CSS in JS",
        skillMainDesc: "CSS in JS。",
        skillDesc: "。",
        skillPointText: {
          1: "Styled Componentsについて理解している",
          2: "CSSモジュールを理解している",
          3: "Emotion, Radium, Glamorousのうち１つを使いこなせる",
          4: "Emotion, Radium, Glamorousのうち２つを使いこなせる",
          5: "Emotion, Radium, Glamorousのうちすべてを使いこなせる",
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
