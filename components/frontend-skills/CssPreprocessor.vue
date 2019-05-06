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
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "CSSプリプロセッサ",
        skillMainDesc: "CSSプリプロセッサ。",
        skillDesc: "CSSのコーディングを効率的にできるスキル。",
        skillPointText: {
          1: "SASS, PostCSS, Lessのうち１つを使いこなせる",
          2: "SASS, PostCSS, Lessのうち２つを使いこなせる",
          3: "SASS, PostCSS, Lessのすべてを使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontCssPre', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontCssPre', this.currentPoint);
    }
  }
</script>
