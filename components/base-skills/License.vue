<template lang="pug">
  div
    // skill
    skill(:img-src="license"
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
  import license from '~/assets/images/license.png';
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
        license,
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "ライセンス",
        skillMainDesc: "ライセンス管理スキル。",
        skillDesc: "OSSの各種ライセンスについて理解し、堅実なソフトウェア開発ができる。",
        skillPointText: {
          1: "OSSとは何か知っている",
          2: "非コピーレフト型について知っている",
          3: "コピーレフト型について知っている",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'baseLicense', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'baseLicense', this.currentPoint);
    }
  }
</script>
