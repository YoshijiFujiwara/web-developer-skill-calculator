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
  import img from '~/assets/images/webserver.jpeg';
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
        skillName: "webサーバのセットアップ",
        skillMainDesc: "webサーバのセットアップ。",
        skillDesc: "webサーバのセットアップ。",
        skillPointText: {
          1: "Apacheサーバのセットアップができる",
          2: "Nginxサーバのセットアップができる",
          3: "Tomcatサーバのセットアップができる",
          4: "IISサーバのセットアップができる",
          5: "Caddyサーバのセットアップができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'baseGit', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'baseGit', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
