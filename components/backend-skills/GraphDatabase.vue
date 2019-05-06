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
    :skill-point-text="skillPointText"
    position="top")

</template>

<script>
  import img from '~/assets/images/neo4j.png';
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
        maxPoint: 1,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "グラフデータベース",
        skillMainDesc: "GraphDatabase。",
        skillDesc: "グラフデータベースの運用方法を理解している",
        skillPointText: {
          1: "グラフデータベースの運用方法を理解している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backGraphDatabase', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backGraphDatabase', this.currentPoint);
    }
  }
</script>
