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
        skillName: "typecheker",
        skillMainDesc: "typecheker。",
        skillDesc: "プログラムのソースコードなどの変更履歴を記録・追跡するための、分散型バージョン管理システムを利用し、開発の効率を上げることができる。",
        skillPointText: {
          1: "バージョン管理ツールについて、聞いたことがある",
          2: "gitを使ったことがある",
          3: "gitの基本的なコマンドを把握している",
          4: "gitの応用的なコマンドを把握している",
          5: "gitを毎日使い、どんなことにも対処することができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'frontTypechecker', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'frontTypechecker', this.currentPoint);
    }
  }
</script>
