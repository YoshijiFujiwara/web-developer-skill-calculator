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
  import img from '~/assets/images/runer-silhouette-running-fast.png';
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
        skillName: "タスクランナー",
        skillMainDesc: "タスクランナー。",
        skillDesc: "Webサイト構築に必要な処理をタスクとして自動化してくれるツールを使いこなすスキル。",
        skillPointText: {
          1: "npm scripts, gulpのいずれかを使える",
          2: "npm scripts, gulpの両方を使える",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontTaskRunner', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontTaskRunner', this.currentPoint);
    }
  }
</script>
