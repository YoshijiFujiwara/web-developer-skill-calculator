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
  import img from '~/assets/images/jenkins.png';
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
        skillName: "CI/CD",
        skillMainDesc: "CI/CD。",
        skillDesc: "CI/CD。",
        skillPointText: {
          1: "Jenkinsを使える",
          2: "TeamCityを使える",
          3: "CircleCIを使える",
          4: "TravisCIを使える",
          5: "Droneを使える",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'devopsCICD', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'devopsCICD', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
