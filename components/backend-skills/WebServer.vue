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
  import img from '~/assets/images/apache.jpeg';
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
        skillName: "Webサーバ",
        skillMainDesc: "WebServer。",
        skillDesc: "各ウェブサーバについて違いを理解している。",
        skillPointText: {
          1: "Apach, Nginx, Caddy, MS IISのうち１つをよく理解している",
          2: "Apach, Nginx, Caddy, MS IISのうち２つをよく理解している",
          3: "Apach, Nginx, Caddy, MS IISのうち３つをよく理解している",
          4: "Apach, Nginx, Caddy, MS IISのうちすべてをよく理解している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backWebServer', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backWebServer', this.currentPoint);
    }
  }
</script>
