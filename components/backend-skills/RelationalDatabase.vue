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
        skillName: "リレーショナルデータベース",
        skillMainDesc: "RelationalDatabase。",
        skillDesc: "リレーショナルデータベースに関する理解度。",
        skillPointText: {
          1: "リレーショナルデータベースとは何か知っている",
          2: "リレーショナルデータベースを使ったことがある",
          3: "Oracle, MySQL, MariaDB, PostgreSQL, MSSQLなどのDBMSの違いを説明できる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backRelationalDatabase', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backRelationalDatabase', this.currentPoint);
    }
  }
</script>
