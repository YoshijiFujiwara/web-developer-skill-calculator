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
  import img from '~/assets/images/Nagios-Logo.jpg';
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
        skillName: "InfrastructureMonitoring",
        skillMainDesc: "InfrastructureMonitoring。",
        skillDesc: "InfrastructureMonitoring。",
        skillPointText: {
          1: "Nagiosを使える",
          2: "Icingaを使える",
          3: "Datadogを使える",
          4: "Zabbixを使える",
          5: "Monitを使える",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'devopsInfrastMonitoring', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'devopsInfrastMonitoring', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
