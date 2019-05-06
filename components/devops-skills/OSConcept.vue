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
  import img from '~/assets/images/os.jpg';
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
        maxPoint: 7,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "OS",
        skillMainDesc: "OSのコンセプト。",
        skillDesc: "OSの基本的なコンセプトを理解している。",
        skillPointText: {
          1: "プロセス制御、スレッド、ソケット、入出力制御、仮想化、メモリ、ファイルシステムのうち１つを理解している",
          2: "プロセス制御、スレッド、ソケット、入出力制御、仮想化、メモリ、ファイルシステムのうち２つを理解している",
          3: "プロセス制御、スレッド、ソケット、入出力制御、仮想化、メモリ、ファイルシステムのうち３つを理解している",
          4: "プロセス制御、スレッド、ソケット、入出力制御、仮想化、メモリ、ファイルシステムのうち４つを理解している",
          5: "プロセス制御、スレッド、ソケット、入出力制御、仮想化、メモリ、ファイルシステムのうち５つを理解している",
          6: "プロセス制御、スレッド、ソケット、入出力制御、仮想化、メモリ、ファイルシステムのうち６つを理解している",
          7: "プロセス制御、スレッド、ソケット、入出力制御、仮想化、メモリ、ファイルシステムのうちすべてを理解している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'devopsSetupWebserver', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'devopsSetupWebserver', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
