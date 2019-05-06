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
  import img from '~/assets/images/elasticsearch.svg';
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
        maxPoint: 3,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "検索エンジン",
        skillMainDesc: "SearchEngine。",
        skillDesc: "大規模アプリケーションにも耐える検索エンジンについて理解している。",
        skillPointText: {
          1: "ElasticSearch, Solr, Sphinxのうち１つを理解している",
          2: "ElasticSearch, Solr, Sphinxのうち２つを理解している",
          3: "ElasticSearch, Solr, Sphinxのうちすべてを理解している",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'backSearchEngine', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'backSearchEngine', this.currentPoint);
    }
  }
</script>
