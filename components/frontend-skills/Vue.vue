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
  import img from '~/assets/images/vue.png';
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
        skillName: "Vue",
        skillMainDesc: "Vue。",
        skillDesc: "Vueを使いこなすことができる。",
        skillPointText: {
          1: "Vueについて、聞いたことがある",
          2: "Vueを使ったことがある",
          3: "Vueで簡単なSPAを作ることができる",
          4: "Vuexも使いこなせる",
          5: "極めた",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontVue', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontVue', this.currentPoint);
    }
  }
</script>
