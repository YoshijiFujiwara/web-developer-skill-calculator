<template lang="pug">
  div
    // skill
    skill(:img-src="git"
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
  import git from '~/assets/images/git.png';
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
        git,
        maxPoint: 5,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "pwa",
        skillMainDesc: "pwa。",
        skillDesc: "Progressive Web Applicationを作ることができる。",
        skillPointText: {
          1: "Storage, Web Sockets, Service Workerについて理解している",
          2: "PRPLパターンを理解している",
          3: "RAIL モデルを理解している",
          4: "パフォーマンスメトリクスを使用している",
          5: "Light Houseなどのツールを使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontPwa', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontPwa', this.currentPoint);
    }
  }
</script>
