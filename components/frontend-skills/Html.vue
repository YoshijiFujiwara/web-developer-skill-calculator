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
        skillName: "HTML",
        skillMainDesc: "HTMLスキル。",
        skillDesc: "webページ開発の基本のスキル。",
        skillPointText: {
          1: "基本的なスクリプトを書くことができる",
          2: "セマンティックなHTMLを書くことができる",
          3: "SEOの基本をおさえている",
          4: "アクセシビリティを考えている",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontHtml', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontHtml', this.currentPoint);
    }
  }
</script>
