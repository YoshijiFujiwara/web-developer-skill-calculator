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
  import img from '~/assets/images/angular.png';
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
        maxPoint: 5,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "Angular",
        skillMainDesc: "Angular。",
        skillDesc: "Angularをつかいこなせる。",
        skillPointText: {
          1: "Angularについて、聞いたことがある",
          2: "Angularを使ったことがある",
          3: "Angularで簡単なSPAを作ることができる",
          4: "RxJSやngrxも使いこなせる",
          5: "極めた",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontAngular', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontAngular', this.currentPoint);
    }
  }
</script>
