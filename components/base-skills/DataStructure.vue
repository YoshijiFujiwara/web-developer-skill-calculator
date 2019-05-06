<template lang="pug">
  div
    // skill
    skill(:img-src="datastruc"
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
  import datastruc from '~/assets/images/datastruc.png';
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
        datastruc,
        maxPoint: 5,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "データ構造とアルゴリズム",
        skillMainDesc: "プログラミングにおける基本的な論理的解決スキル。",
        skillDesc: "プログラミングに必要な、データ構造やアルゴリズムを理解し、それを反映したコーディングをすることができる。",
        skillPointText: {
          1: "データ構造、アルゴリズムとは何か知っている",
          2: "データ構造、アルゴリズムの基本を知っている",
          3: "データ構造、アルゴリズムの基本を知ったうえで、使いこなすことができる",
          4: "データ構造、アルゴリズムを幅広く知っており、他人に説明もできる",
          5: "データ構造、アルゴリズムの複雑な問題を、短時間で解くことができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'baseDataStructure', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'baseDataStructure', this.currentPoint);
    }
  }
</script>
