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
  import img from '~/assets/images/nosql.jpeg';
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
        skillName: "NoSql",
        skillMainDesc: "NoSql。",
        skillDesc: "MongoDBなどのNoSqlをつかいこなす能力。",
        skillPointText: {
          1: "NoSqlとは何か知っている",
          2: "NoSqlを使ったことがある",
          3: "NoSqlを使ってアプリケーションを作ることができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backNoSql', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backNoSql', this.currentPoint);
    }
  }
</script>
