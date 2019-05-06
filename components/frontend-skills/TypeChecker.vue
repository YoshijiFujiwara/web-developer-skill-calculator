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
        maxPoint: 2,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "タイプチェッカー",
        skillMainDesc: "typecheker。",
        skillDesc: "型安全なAltjsを使いこなせる。",
        skillPointText: {
          1: "TypeScriptを使いこなせる",
          2: "Flowも使える",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontTypechecker', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontTypechecker', this.currentPoint);
    }
  }
</script>
