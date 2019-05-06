<template lang="pug">
  div
    // skill
    small-skill(:img-src="img"
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
  import img from '~/assets/images/erlang.png';
  import SmallSkill from '~/components/SmallSkill';
  import SkillCard from '~/components/SkillCard';


  export default {
    props: ["clickable"],
    components: {
      SmallSkill,
      SkillCard
    },
    data() {
      return {
        img,
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "Erlang",
        skillMainDesc: "アーランと読む。",
        skillDesc: "分散平行処理を主な目的としてエリクソンが開発した。現在はオープンソース化されている",
        skillPointText: {
          1: "基本的な文法を理解している",
          2: "簡単なアプリケーションを作成できる",
          3: "大規模なアプリケーションを開発できる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backErlang', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backErlang', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
