<template lang="pug">
  div.skill(:style="edgeColor")
    div.inner-skill
      v-img.skill-image(contain :src="imgSrc")
      div.point-display(:style="edgeColor" v-if="clickable")
        span.point-span
          p.text-xs-center.point-text {{currentPoint}}/{{maxPoint}}

</template>

<script>
  export default {
    props: ["img-src", "max-point", "skill-name", "skill-desc", "current-point", "clickable"],
    data() {
      return {
      }
    },
    computed: {
      edgeColor() {
        let color = '';
        if (this.currentPoint === 0) {
          color =  "lightgrey";
        } else if (this.currentPoint < this.maxPoint) {
          color = "red";
        } else if (this.currentPoint === this.maxPoint) {
          color = "green";
        }

        return `background-color: ${color}`;
      }
    }
  }
</script>

<style lang="scss" scoped>

  .skill {
    height: 100px;
    width: 100px;
    background-color: bisque;
    -webkit-border-radius: 20px;
    -moz-border-radius: 20px;
    border-radius: 20px;
    border: double 7px black;
    position: relative;

    .inner-skill {
      position: absolute;
      width: 100%;
      height: 100%;
      background-color: white;
      -webkit-border-radius: 15px;
      -moz-border-radius: 15px;
      border-radius: 15px;
    }
  }

  .skill-image {
    -webkit-border-radius: 15px;
    -moz-border-radius: 15px;
    border-radius: 15px;
  }

  $point_display_width: 80px;
  $point_display_height: 34px;
  $point_display_breadth: 6px;

  .point-display {
    position: absolute;
    width: $point_display_width;
    height: $point_display_height;
    border: double $point_display_breadth black;
    right: -14px;
    bottom: -14px;
    padding: 4px;

    -webkit-border-top-left-radius:7px;
    -webkit-border-bottom-right-radius:7px;
    -moz-border-radius-topleft:7px;
    -moz-border-radius-bottomright:7px;
    border-top-left-radius:7px;
    border-bottom-right-radius:7px;
  }

  .point-span {
    position: absolute;
    background-color: black;
    width: $point_display_width - ($point_display_breadth * 2);
    height: $point_display_height - ($point_display_breadth * 2);
    right: 0px;
    bottom: 0px;
  }

  .point-text {
    font-size: 25px;
    font-weight: 900;
    line-height: 25px;

    color: white;
    -webkit-text-stroke: 1px black;
    text-stroke: 1px black;
  }
</style>
