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
  import img from '~/assets/images/webpack.png';
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
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "ModuleBundler",
        skillMainDesc: "ModuleBundler。",
        skillDesc: "モジュールバンドラーを使いこなせる。",
        skillPointText: {
          1: "webpack, Parcel, Rollupのうち１つを使いこなせる",
          2: "webpack, Parcel, Rollupのうち２つを使いこなせる",
          3: "webpack, Parcel, Rollupのうちすべてを使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontModuleBundler', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontModuleBundler', this.currentPoint);
    }
  }
</script>
