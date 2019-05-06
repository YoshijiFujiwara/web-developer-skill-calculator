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
  import img from '~/assets/images/css-3.png';
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
        maxPoint: 4,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "CSS",
        skillMainDesc: "CSSスキル。",
        skillDesc: "webページを自由にデザインするスキル。",
        skillPointText: {
          1: "基本的なCSSの書き方がわかる",
          2: "レイアウトができる(float, position, display, box model, css grid, flex box)",
          3: "メディアクエリを使うことができる",
          4: "CSS3の機能も使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontCss', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontCss', this.currentPoint);
    }
  }
</script>
