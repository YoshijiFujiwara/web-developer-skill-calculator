<template lang="pug">
  // skill 説明のcard？？
  div.skill-card
    div.inner-skill-card.px-3.pt-2
      h3.skill-card-title {{skillName}}
      p.skill-card-desc
        span.skill-card-desc-feature {{skillMainDesc}}
        | {{skillDesc}}

      div.skill-card-current(v-if="currentPoint !== 0")
        p.label 今のレベル
        p {{skillPointText[currentPoint]}}

      div.skill-card-next-level(v-if="currentPoint != maxPoint")
        p.label 次のレベル
        p {{skillPointText[currentPoint + 1]}}
</template>

<script>
  export default {
    props: ["skill-name", "skill-main-desc", "skill-desc", "current-point", "max-point", "skill-point-text"]
  }
</script>

<style lang="scss" scoped>
  $card_height: 400px;
  $card_width: 500px;
  $card_border_breadth: 10px;

  .skill-card {
    position: absolute;
    z-index: 100;
    height: $card_height;
    width: $card_width;
    border: double $card_border_breadth black;
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    border-radius: 10px;
    background-color: yellow;

    -webkit-text-stroke: 1px black;
    text-stroke: 1px black;

    .inner-skill-card {
      position: absolute;
      z-index: 100;
      height: $card_height - ($card_border_breadth * 2);
      width: $card_width - ($card_border_breadth * 2);
      -webkit-border-radius: 1px;
      -moz-border-radius: 1px;
      border-radius: 1px;
      background: linear-gradient(0.25turn, #2f314a, #32649f, #2f314a);

      .skill-card-title {
        font-weight: 900;
        font-size: 30px;
        color: #7ee8ea;
      }

      .skill-card-desc {
        font-weight: 900;
        font-size: 17px;
        color: white;

        .skill-card-desc-feature {
          color: #f7d84b;
          font-size: 18px;
        }
      }

      .skill-card-current {
        font-weight: 900;
        font-size: 17px;
        color: white;

        .label {
          font-size: 19px;
          margin-bottom: 0px;
        }
      }

      .skill-card-next-level {
        color: #bc5139;
        font-size: 17px;
        font-weight: 900;

        .label {
          font-size: 19px;
          margin-bottom: 0px;
        }
      }
    }
  }
</style>
