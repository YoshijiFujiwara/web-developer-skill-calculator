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
  import img from '~/assets/images/appdynamics.png';
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
        maxPoint: 2,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "ApplicationMonitoring",
        skillMainDesc: "ApplicationMonitoring。",
        skillDesc: "プログラムのソースコードなどの変更履歴を記録・追跡するための、分散型バージョン管理システムを利用し、開発の効率を上げることができるApplicationMonitoring。",
        skillPointText: {
          1: "AppDynamicsを使える",
          2: "New Relicを使える",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'devopsApplicationMonitoring', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'devopsApplicationMonitoring', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
