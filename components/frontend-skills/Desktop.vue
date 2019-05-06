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
  import img from '~/assets/images/electron.png';
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
        skillName: "デスクトップアプリケーション",
        skillMainDesc: "desktop。",
        skillDesc: "デスクトップアプリケーションを作成することができる。",
        skillPointText: {
          1: "Electron, Proton Native, Carloのうち１つを使いこなせる",
          2: "Electron, Proton Native, Carloのうち２つを使いこなせる",
          3: "Electron, Proton Native, Carloのうちすべてを使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontDesktop', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontDesktop', this.currentPoint);
    }
  }
</script>
