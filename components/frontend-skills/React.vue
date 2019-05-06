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
  import img from '~/assets/images/react.png';
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
        skillName: "React",
        skillMainDesc: "React。",
        skillDesc: "React.jsを使いこなせる。",
        skillPointText: {
          1: "React.jsについて、聞いたことがある",
          2: "React.jsを使ったことがある",
          3: "React.jsで簡単なSPAを作ることができる",
          4: "ReduxやMobXも使いこなせる",
          5: "極めた",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontReact', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontReact', this.currentPoint);
    }
  }
</script>
