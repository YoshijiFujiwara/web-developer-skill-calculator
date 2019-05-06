<template lang="pug">
  div
    // skill
    skill(:img-src="github"
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
  import github from '~/assets/images/github.png';
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
        github,
        maxPoint: 5,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "github",
        skillMainDesc: "gitを利用した便利なwebサービス。",
        skillDesc: "世界中の人々が自分の作品(プログラムコードやデザインデータなど)を保存、公開することができるようにしたウェブサービスを効果的に活用することができる。",
        skillPointText: {
          1: "githubについて聞いたことがある",
          2: "githubのアカウントを持っている",
          3: "githubにリポジトリを作ったことがある",
          4: "githubを利用し、複数人で作業したことがある",
          5: "githubを利用して、ライブラリ開発などに貢献したことがある",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'baseGithub', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'baseGithub', this.currentPoint);
    }
  }
</script>
