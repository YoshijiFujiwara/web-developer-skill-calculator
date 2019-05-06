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
        maxPoint: 5,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "LinterFormatter",
        skillMainDesc: "LinterFormatter。",
        skillDesc: "リアルタイム構文チェックツールで効率を上げることができる。",
        skillPointText: {
          1: "Prettire, ESLint, JSHint, JSLint, JSCSのうち１つを使いこなすことができる",
          2: "Prettire, ESLint, JSHint, JSLint, JSCSのうち２つを使いこなすことができる",
          3: "Prettire, ESLint, JSHint, JSLint, JSCSのうち３つを使いこなすことができる",
          4: "Prettire, ESLint, JSHint, JSLint, JSCSのうち４つを使いこなすことができる",
          5: "Prettire, ESLint, JSHint, JSLint, JSCSのすべてを使いこなすことができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontLinter', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontLinter', this.currentPoint);
    }
  }
</script>
