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
        skillName: "パッケージマネージャ",
        skillMainDesc: "パッケージマネージャ。",
        skillDesc: "パッケージ管理ツールを使いこなすスキル。",
        skillPointText: {
          1: "パッケージ管理について理解している",
          2: "npm, yarn のどちらかを使いこなせる",
          3: "npm, yarn の両方を使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontPackageManager', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontPackageManager', this.currentPoint);
    }
  }
</script>
