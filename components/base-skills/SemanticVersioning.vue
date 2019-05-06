<template lang="pug">
  div
    // skill
    skill(:img-src="semantic"
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
  import semantic from '~/assets/images/semantic-versioning.png';
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
        semantic,
        maxPoint: 2,
        currentPoint: 0,
        skillName: "セマンティックバージョニング",
        skillMainDesc: "バージョンナンバー管理スキル。",
        skillDesc: "バージョンごとの理想的なナンバリング方法を知っており、使いこなすことができる。",
        skillPointText: {
          1: "セマンティックバージョニングについて、聞いたことがある",
          2: "セマンティックバージョニングの３つの数字、それぞれの意味を説明することができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'baseSemantic', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'baseSemantic', this.currentPoint);
    }
  }
</script>
