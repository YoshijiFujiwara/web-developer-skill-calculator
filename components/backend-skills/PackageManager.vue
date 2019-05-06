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
  import img from '~/assets/images/npm.png';
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
        maxPoint: 2,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "パッケージマネージャ",
        skillMainDesc: "PackageManager。",
        skillDesc: "パッケージマネージャの使い方を心得ている。(例)PHP: composer, Node.js: NPM and yarn, Python: pip, Ruby:gems",
        skillPointText: {
          1: "パッケージマネージャとは何か知っている",
          2: "パッケージマネージャを使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backBackendPackageManager', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backBackendPackageManager', this.currentPoint);
    }
  }
</script>
