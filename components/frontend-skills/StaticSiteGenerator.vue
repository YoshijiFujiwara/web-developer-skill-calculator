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
  import img from '~/assets/images/gatsby.jpeg';
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
        skillName: "静的サイトジェネレーター",
        skillMainDesc: "静的サイトジェネレーター。",
        skillDesc: "静的サイトジェネレーターを使いこなせる。",
        skillPointText: {
          1: "GatsbyJSを使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontStaticSite', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontStaticSite', this.currentPoint);
    }
  }
</script>
