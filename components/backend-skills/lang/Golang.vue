<template lang="pug">
  div
    // skill
    small-skill(:img-src="img"
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
  import img from '~/assets/images/golang.jpeg';
  import SmallSkill from '~/components/SmallSkill';
  import SkillCard from '~/components/SkillCard';


  export default {
    props: ["clickable"],
    components: {
      SmallSkill,
      SkillCard
    },
    data() {
      return {
        img,
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "Golang",
        skillMainDesc: "マスコットが、、。",
        skillDesc: "人気だ",
        skillPointText: {
          1: "基本的な文法を理解している",
          2: "簡単なアプリケーションを作成できる",
          3: "大規模なアプリケーションを開発できる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backGolang', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backGolang', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
