<template lang="pug">
  div
    // skill
    skill(:img-src="charEnco"
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
  import charEnco from '~/assets/images/char-enco.png';
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
        charEnco,
        maxPoint: 3,
        currentPoint: 0,
        skillName: "文字エンコーディング",
        skillMainDesc: "文字コード把握スキル。",
        skillDesc: "文字コードについて理解している。",
        skillPointText: {
          1: "文字コードについて、聞いたことがある",
          2: "文字コードを理解している",
          3: "文字エンコーディングを理解している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'baseCharacterEncoding', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'baseCharacterEncoding', this.currentPoint);
    }
  }
</script>
