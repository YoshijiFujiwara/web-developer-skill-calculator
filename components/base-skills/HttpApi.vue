<template lang="pug">
  div
    // skill
    skill(:img-src="httpapi"
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
  import httpapi from '~/assets/images/httpapi.png';
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
        httpapi,
        maxPoint: 3,
        currentPoint: 0,
        skillName: "HTTP/HTTPS API",
        skillMainDesc: "通信プロトコル把握スキル。",
        skillDesc: "HTTP, HTTPSなどの通信プロトコルを理解し、また、APIについても理解している。",
        skillPointText: {
          1: "HTTPについて知っている",
          2: "HTTPSについて知っている",
          3: "APIについて知っている",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'httpapi', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'httpapi', this.currentPoint);
    }
  }
</script>
