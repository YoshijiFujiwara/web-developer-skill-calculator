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
        maxPoint: 5,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "認証",
        skillMainDesc: "Authentication。",
        skillDesc: "OAuthやJWTなどの認証機構について理解し、アプリケーションに組み込むことができる。",
        skillPointText: {
          1: "基本的な認証機構について理解している",
          2: "OAuth, トークン認証, JWT, OpenIDのうち１つを理解し、アプリケーションに組み込むことができる",
          3: "OAuth, トークン認証, JWT, OpenIDのうち２つを理解し、アプリケーションに組み込むことができる",
          4: "OAuth, トークン認証, JWT, OpenIDのうち３つを理解し、アプリケーションに組み込むことができる",
          5: "OAuth, トークン認証, JWT, OpenIDのうちすべてを理解し、アプリケーションに組み込むことができる",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backAuthentication', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backAuthentication', this.currentPoint);
    }
  }
</script>
