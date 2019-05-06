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
  import img from '~/assets/images/elkstack.png';
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
        skillName: "ログ管理",
        skillMainDesc: "ログ管理。",
        skillDesc: "ログ管理。",
        skillPointText: {
          1: "ELK Stackを使える",
          2: "Graylogを使える",
          3: "Splunkを使える",
          4: "Papertrailを使える",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'devopsLogManagement', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'devopsLogManagement', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
