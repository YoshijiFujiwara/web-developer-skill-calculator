<template lang="pug">
  div
    // skill
    skill(:img-src="terminal"
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
  import terminal from '~/assets/images/terminal.png';
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
        terminal,
        maxPoint: 2,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "スタンダードとベストプラクティス",
        skillMainDesc: "StandardandBestPractice。",
        skillDesc: "それぞれの言語のもつスタンダードやベストプラクティスについて理解している。(例)PHP: PHP-FIG, PSRs,",
        skillPointText: {
          1: "それらが何か知っている",
          2: "それらを意識してコーディングしている",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backStandardAndBestPractice', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backStandardAndBestPractice', this.currentPoint);
    }
  }
</script>
