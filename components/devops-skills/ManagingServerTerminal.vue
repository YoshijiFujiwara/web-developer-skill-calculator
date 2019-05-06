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
  import img from '~/assets/images/terminal_server.png';
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
        maxPoint: 8,
        currentPoint: 0,
        skillDescShow: false,
        skillName: "ターミナルによるサーバーの制御",
        skillMainDesc: "ターミナルによるサーバーの制御。",
        skillDesc: "ターミナルによるサーバーの制御。",
        skillPointText: {
          1: "Bashスクリプトが書ける",
          2: "Vim/Nano/PowerShell/Emacsを使える",
          3: "gcc, makeなどを使ってソースからアプリケーションのコンパイルができる",
          4: "nmon, iostat, sar, vmstatなどのコマンドを使い、システムパフォーマンスを管理できる",
          5: "テキストの操作ができる。(awk, sed, grep, sort, uniq, cat, cut, echo, fmt, tr, nl, egrep, fgrep, wc)",
          6: "プロセスのモニタリングができる。(ps, top, htop, atop, lsof)",
          7: "ネットワーク系コマンドが使える。(nmap, tcpdump, ping, mtr, traceroute, airmon, dig, iptables)",
          8: "その他のコマンドが使える。(strace, dtrace, systemtap, uname, df, history)",
        }
      }
    },
    watch: {
      currentPoint() {
        this.$emit('set-skill-points', 'devopsManagingServerTerminal', this.currentPoint);
      }
    },
    created() {
      this.$emit('set-skill-points', 'devopsManagingServerTerminal', this.currentPoint);
    },
    methods: {
      updateCurrentPoint(newPoint) {
        console.log(newPoint);
        this.currentPoint = newPoint;
      }
    }
  }
</script>
