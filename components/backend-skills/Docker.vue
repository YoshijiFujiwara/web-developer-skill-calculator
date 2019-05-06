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
        maxPoint: 1,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "docker",
        skillMainDesc: "docker。",
        skillDesc: "dockerを使いこなせる。",
        skillPointText: {
          1: "dockerを使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backDocker', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backDocker', this.currentPoint);
    }
  }
</script>
