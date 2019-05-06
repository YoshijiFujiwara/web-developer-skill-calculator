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
  import img from '~/assets/images/connection.png';
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
        maxPoint: 6,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "ネットワークとセキュリティ",
        skillMainDesc: "ネットワークとセキュリティ。",
        skillDesc: "ネットワークとセキュリティ。",
        skillPointText: {
          1: "DNS, OSIモデル, HTTP, HTTPS, FTP, SSL/TLSのうち１つを理解している",
          2: "DNS, OSIモデル, HTTP, HTTPS, FTP, SSL/TLSのうち２つを理解している",
          3: "DNS, OSIモデル, HTTP, HTTPS, FTP, SSL/TLSのうち３つを理解している",
          4: "DNS, OSIモデル, HTTP, HTTPS, FTP, SSL/TLSのうち４つを理解している",
          5: "DNS, OSIモデル, HTTP, HTTPS, FTP, SSL/TLSのうち５つを理解している",
          6: "DNS, OSIモデル, HTTP, HTTPS, FTP, SSL/TLSのうちすべてを理解している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'devopsNetworkAndSecurity', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'devopsNetworkAndSecurity', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
