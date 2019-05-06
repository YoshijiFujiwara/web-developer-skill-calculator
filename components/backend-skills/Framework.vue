<template lang="pug">
  div
    // skill
    skill(:img-src="terminal"
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
  import terminal from '~/assets/images/terminal.png';
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
        terminal,
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "Framework",
        skillMainDesc: "Framework。",
        skillDesc: "フレームワークを使って、大規模アプリケーションを効率的に開発する能力。PHP - Laravel または Symfony, Slim, Lumen。Node.js - Express.js。Golang - フレームワークなし",
        skillPointText: {
          1: "フレームワークとは何か知っている",
          2: "フレームワークを使ったことがある",
          3: "フレームワークでアプリケーションを作成することができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backFramework', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backFramework', this.currentPoint);
    }
  }
</script>
