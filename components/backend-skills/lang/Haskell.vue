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
  import img from '~/assets/images/haskell.png';
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
        skillName: "HasKell",
        skillMainDesc: "純粋な",
        skillDesc: "関数型プログラミング言語である。",
        skillPointText: {
          1: "基本的な文法を理解している",
          2: "簡単なアプリケーションを作成できる",
          3: "大規模なアプリケーションを開発できる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backHaskell', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backHaskell', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
