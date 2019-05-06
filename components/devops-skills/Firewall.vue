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
  import img from '~/assets/images/firewall.png';
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
        skillName: "Firewall",
        skillMainDesc: "Firewall。",
        skillDesc: "Firewall。",
        skillPointText: {
          1: "ファイアウォール、リバースプロキシ、フォワードプロキシ、ロードバランサ、キャッシュサーバのうち１つを理解している",
          2: "ファイアウォール、リバースプロキシ、フォワードプロキシ、ロードバランサ、キャッシュサーバのうち２つを理解している",
          3: "ファイアウォール、リバースプロキシ、フォワードプロキシ、ロードバランサ、キャッシュサーバのうち３つを理解している",
          4: "ファイアウォール、リバースプロキシ、フォワードプロキシ、ロードバランサ、キャッシュサーバのうち４つを理解している",
          5: "ファイアウォール、リバースプロキシ、フォワードプロキシ、ロードバランサ、キャッシュサーバのうちすべてを理解している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'devopsFirewall', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'devopsFirewall', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
