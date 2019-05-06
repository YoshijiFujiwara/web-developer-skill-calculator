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
  import img from '~/assets/images/package.png';
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
        skillName: "MakePackageOrLibrary",
        skillMainDesc: "MakePackageOrLibrary。",
        skillDesc: "CUIシェルソフトを利用し、UNIX系OSを自在に操る能力。",
        skillPointText: {
          1: "ターミナルとは何か知っている",
          2: "ターミナルを使ったことがある",
          3: "ターミナルの基本的なコマンドを把握している",
          4: "ターミナルの応用的なコマンドを把握している",
          5: "ターミナルを毎日使い、どんな複雑な作業も、スクリプトで解決している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backMakePackageOrLibrary', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backMakePackageOrLibrary', this.currentPoint);
    }
  }
</script>
