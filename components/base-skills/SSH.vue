<template lang="pug">
  div
    // skill
    skill(:img-src="ssh"
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
  import ssh from '~/assets/images/ssh.png';
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
        ssh,
        maxPoint: 3,
        currentPoint: 0,
        skillName: "ssh",
        skillMainDesc: "リモートコンピュータとの通信スキル。",
        skillDesc: "暗号や認証の技術を利用して、安全にリモートコンピュータと通信し、作業を行うことができる。",
        skillPointText: {
          1: "sshについて、聞いたことがある",
          2: "sshを使ったことがある",
          3: "sshを毎日使い、どんなことにも対処することができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'baseSsh', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'baseSsh', this.currentPoint);
    }
  }
</script>
