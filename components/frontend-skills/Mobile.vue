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
        maxPoint: 2,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "モバイルアプリケーション",
        skillMainDesc: "mobile application。",
        skillDesc: "モバイルアプリケーションを作成することができる。",
        skillPointText: {
          1: "React Nativeでモバイルアプリケーションを作成することができる",
          2: "NativeScriptでモバイルアプリケーションを作成することができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontMobile', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontMobile', this.currentPoint);
    }
  }
</script>
