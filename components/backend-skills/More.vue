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
  import img from '~/assets/images/round-add-button.png';
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
        maxPoint: 4,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "さらに",
        skillMainDesc: "More。",
        skillDesc: "さらに。",
        skillPointText: {
          1: "プロファイリング、静的解析、DDD、SOAP、のうち１つを理解している",
          2: "プロファイリング、静的解析、DDD、SOAP、のうち２つを理解している",
          3: "プロファイリング、静的解析、DDD、SOAP、のうち３つを理解している",
          4: "プロファイリング、静的解析、DDD、SOAP、のうちすべてを理解している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backMore', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backMore', this.currentPoint);
    }
  }
</script>
