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
        maxPoint: 4,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "サーバーサイドレンダリング",
        skillMainDesc: "ssr。",
        skillDesc: "ssrを使いこなせる。",
        skillPointText: {
          1: "Next.js(React), After.js(React), Universal(Angular), Nuxt.js(Vue)のうち１つを使いこなせる",
          2: "Next.js(React), After.js(React), Universal(Angular), Nuxt.js(Vue)のうち２つを使いこなせる",
          3: "Next.js(React), After.js(React), Universal(Angular), Nuxt.js(Vue)のうち３つを使いこなせる",
          4: "Next.js(React), After.js(React), Universal(Angular), Nuxt.js(Vue)のうちすべてを使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontSsr', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontSsr', this.currentPoint);
    }
  }
</script>
