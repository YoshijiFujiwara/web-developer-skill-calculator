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
  import img from '~/assets/images/websocket.png';
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
        maxPoint: 1,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "WebSocket",
        skillMainDesc: "WebSocket。",
        skillDesc: "ウェブソケットを使える。",
        skillPointText: {
          1: "ウェブソケットを使える",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backWebSocket', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backWebSocket', this.currentPoint);
    }
  }
</script>
