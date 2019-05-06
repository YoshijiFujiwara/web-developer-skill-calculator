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
    :skill-point-text="skillPointText"
    position="top")

</template>

<script>
  import img from '~/assets/images/aws.jpeg';
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
        skillName: "Cloud Provider",
        skillMainDesc: "Cloud Provider。",
        skillDesc: "Cloud Provider。",
        skillPointText: {
          1: "AWS, Google Cloud, Azure, Digital Ocean, Herokuのうち１つを使える",
          2: "AWS, Google Cloud, Azure, Digital Ocean, Herokuのうち２つを使える",
          3: "AWS, Google Cloud, Azure, Digital Ocean, Herokuのうち３つを使える",
          4: "AWS, Google Cloud, Azure, Digital Ocean, Herokuのうち４つを使える",
          5: "AWS, Google Cloud, Azure, Digital Ocean, Herokuのうちすべてを使える",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'devopsCloudProvider', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'devopsCloudProvider', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
