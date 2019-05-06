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
  import img from '~/assets/images/rabbitmq.png';
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
        maxPoint: 2,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "メッセージブローカ",
        skillMainDesc: "MessageBrokers。",
        skillDesc: "メッセージブローカとは何か理解している。",
        skillPointText: {
          1: "RabbitMQ, Kafkaのうち１つを理解し、使いこなせる",
          2: "RabbitMQ, Kafkaのうちすべてを理解し、使いこなせる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backMessageBrokers', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backMessageBrokers', this.currentPoint);
    }
  }
</script>
