<template lang="pug">
  div
    // skill
    skill(:img-src="git"
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
  import git from '~/assets/images/git.png';
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
        git,
        maxPoint: 4,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "CSSフレームワーク",
        skillMainDesc: "CSSフレームワーク。",
        skillDesc: "CSSのフレームワークを用いて、効率的にデザインを行うことができる。",
        skillPointText: {
          1: "Bootstrap, Materialize CSS, Bulma, Semantic UIのうち１つを使いこなせる",
          2: "Bootstrap, Materialize CSS, Bulma, Semantic UIのうち２つを使いこなせる",
          3: "Bootstrap, Materialize CSS, Bulma, Semantic UIのうち３つを使いこなせる",
          4: "Bootstrap, Materialize CSS, Bulma, Semantic UIのすべてを使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontFramework', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontFramework', this.currentPoint);
    }
  }
</script>
