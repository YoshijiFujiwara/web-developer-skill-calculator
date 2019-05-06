<template lang="pug">
  v-layout(column justify-center align-center)
    div.skill-container.mb-5
      // base-skilltree
      div#base-skilltree.mb-5(:style="baseSkillTreeStyle")
        div#base-inner.px-2.pt-3(:style="baseSkillTreeInnerStyle")
          h1#base-skilltree-title BASE {{currentBasePoint}}
          v-layout(row justify-space-between)
            git(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            basic-terminal-usage(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            data-structure(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            solid(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            git-hub(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            license(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            semantic-versioning(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            s-s-h(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            http-api(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            design-pattern(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
            character-encoding(v-on:set-skill-points="setBaseSkillPoint" :clickable="true")
      div {{currentBasePoint}}
      v-layout(row fluid)
        // front-end tree
        div.skilltree#frontend-tree.mr-3
          div.inner-skilltree.px-2.pt-3
            h1#frontend-skilltree-title FRONTEND 12
            // 第1階層
            v-layout.mb-3(row justify-space-between)
              html-skill(v-on:set-skill-points="setBaseSkillPoint" :clickable="clickableFront1")
              css-skill(v-on:set-skill-points="setBaseSkillPoint" :clickable="clickableFront1")
              javascript(v-on:set-skill-points="setBaseSkillPoint" :clickable="clickableFront1")
            // 第2階層
            v-layout.mb-3(row justify-center)
              package-manager
            // 第3階層
            v-layout.mb-3(row justify-space-between)
              css-preprocessor
              css-framework
              css-architecture
            // 第4階層
            v-layout.mb-3(row justify-space-between)
              linter
              module-bundler
              task-runner
            // 第5階層
            v-layout.mb-3(row justify-space-between)
              react
              angular
              vue-skill
            // 第6階層
            v-layout.mb-3(row justify-center)
              test
            // 第7階層
            v-layout.mb-3(row justify-center)
              type-checker
            // 第8階層
            v-layout.mb-3(row justify-space-between)
              pwa
              ssr
            // 第9階層
            v-layout.mb-3(row justify-space-between)
              static-site-generator
              mobile
              desktop
            // 第10階層
            v-layout.mb-3(row justify-center)
              web-assembly

        // back-end tree
        div.skilltree#backend-tree.mx-3
            git

        // dev-ops tree
        div.skilltree#devops-tree.ml-3

</template>

<script>
  import star from '~/assets/images/star.png';
  import Skill from '~/components/Skill';
  // basic skills
  import Git from '~/components/base-skills/Git';
  import BasicTerminalUsage from '~/components/base-skills/BasicTerminalUsage';
  import DataStructure from '~/components/base-skills/DataStructure';
  import Solid from '~/components/base-skills/Solid';
  import GitHub from '~/components/base-skills/GitHub';
  import License from '~/components/base-skills/License';
  import SemanticVersioning from '~/components/base-skills/SemanticVersioning';
  import SSH from '~/components/base-skills/SSH';
  import HttpApi from '~/components/base-skills/HttpApi';
  import DesignPattern from '~/components/base-skills/DesignPattern';
  import CharacterEncoding from '~/components/base-skills/CharacterEncoding';

  // front-end
  import HtmlSkill from '~/components/frontend-skills/Html';
  import CssSkill from '~/components/frontend-skills/Css';
  import Javascript from '~/components/frontend-skills/Javascript';
  import PackageManager from '~/components/frontend-skills/PackageManager';
  import CssPreprocessor from '~/components/frontend-skills/CssPreprocessor';
  import CssFramework from '~/components/frontend-skills/CssFramework';
  import CssArchitecture from '~/components/frontend-skills/CssArchitecture';
  import Linter from '~/components/frontend-skills/Linter';
  import ModuleBundler from '~/components/frontend-skills/ModuleBundler';
  import TaskRunner from '~/components/frontend-skills/TaskRunner';
  import React from '~/components/frontend-skills/React';
  import Angular from '~/components/frontend-skills/Angular';
  import VueSkill from '~/components/frontend-skills/Vue';
  import Test from '~/components/frontend-skills/Test';
  import Pwa from '~/components/frontend-skills/Pwa';
  import TypeChecker from '~/components/frontend-skills/TypeChecker';
  import Ssr from '~/components/frontend-skills/Ssr';
  import StaticSiteGenerator from '~/components/frontend-skills/StaticSiteGenerator';
  import Desktop from '~/components/frontend-skills/Desktop';
  import Mobile from '~/components/frontend-skills/Mobile';
  import WebAssembly from '~/components/frontend-skills/WebAssembly';

  export default {
    components: {
      Skill,
      Git,
      BasicTerminalUsage,
      DataStructure,
      Solid,
      GitHub,
      License,
      SemanticVersioning,
      SSH,
      HttpApi,
      DesignPattern,
      CharacterEncoding,
      HtmlSkill,
      CssSkill,
      Javascript,
      PackageManager,
      CssPreprocessor,
      CssFramework,
      CssArchitecture,
      Linter,
      ModuleBundler,
      TaskRunner,
      React,
      Angular,
      VueSkill,
      Test,
      Pwa,
      TypeChecker,
      Ssr,
      StaticSiteGenerator,
      Desktop,
      Mobile,
      WebAssembly
    },
    data() {
      return {
        star,
        skillDialog: false,

        // それぞれのスキルツリーのポイント合計値
        baseSkillPointData: {},
        frontendSkillPointData: {},
        backendSkillPointData: {},
        devopsSkillPointData: {},

        // baseskill のそれぞれのポイント
        baseGit: 0,
        baseTerminal: 0,
        baseDataStructure: 0,
        baseSolid: 0,
        baseGithub: 0,
        baseLicense: 0,
        baseSemantic: 0,
        baseSsh: 0,
        baseDesignPattern: 0,
        baseCharacterEncoding: 0,

        // frontendskillのそれぞれのポイント
        frontHtml: 0,
        frontCss: 0,
        frontJavascript: 0,
        frontPackageManager: 0,
        frontCssPre: 0,
        frontFramework: 0,
        frontArchitecture: 0,
        frontLinter: 0,
        frontModuleBundler: 0,
        frontTaskRunner: 0,
        frontReact: 0,
        frontAngular: 0,
        frontVue: 0,
        frontTesting: 0,
        frontPwa: 0,
        frontTypechecker: 0,
        frontSsr: 0,
        frontStaticSite: 0,
        frontDesktop: 0,
        frontMobile: 0,
        frontWebAssembly: 0,
      }
    },
    methods: {
      test() {
        console.log('hogehoge')
      },
      showSkillDesc(hoge) {
        // console.log(hoge)
        // this.$emit('show-skill-desc', '')
      },

      // base skillのポイントをセット
      setBaseSkillPoint(name, currentPoint) {
        switch (name) {
          case 'git':
            this.baseGit = currentPoint; break;
          case 'terminal':
            this.baseTerminal = currentPoint; break;
          case 'datastruc':
            this.baseDataStructure = currentPoint; break;
          case 'solid':
            this.baseSolid = currentPoint; break;
          case 'github':
            this.baseGithub = currentPoint; break;
          case 'license':
            this.baseLicense = currentPoint; break;
          case 'semantic':
            this.baseSemantic = currentPoint; break;
          case 'ssh':
            this.baseSsh = currentPoint; break;
          case 'designpattern':
            this.baseDesignPattern = currentPoint; break;
          case 'char-enco':
            this.baseCharacterEncoding = currentPoint; break;
          default: break;
        }
      },
    },

    computed: {
      // base
      currentBasePoint() {
        const sum = this.baseGit + this.baseTerminal + this.baseDataStructure + this.baseSolid + this.baseGithub + this.baseLicense +
                    this.baseSemantic + this.baseSsh + this.baseDesignPattern + this.baseCharacterEncoding;

        return sum;
      },
      baseSkillTreeStyle() {
        if (this.currentBasePoint < 10) {
          return `background-color: lightgrey`;
        } else {
          return `background-color: yellow`;
        }
      },
      baseSkillTreeInnerStyle() {
        const border = (this.currentBasePoint / 10) * 100;
        return `background:linear-gradient(180deg,#c7ce00 -30%,#c7ce00 ${border}%,grey ${border}%,grey 150%);`;
      },

      // front
      currentFrontPoint() {
        const sum = this.frontHtml + this.frontCss + this.frontJavascript + this.frontPackageManager + this.frontCssPre + this.frontFramework + this.frontArchitecture + this.frontLinter + this.frontModuleBundler + this.frontTaskRunner + this.frontReact + this.frontAngular + this.frontVue + this.frontTesting + this.frontPwa + this.frontTypechecker + this.frontSsr + this.frontStaticSite + this.frontDesktop + this.frontMobile + this.frontWebAssembly;
        return sum;
      },

      // ポイント加算条件
      clickableFront1() {
        return this.currentBasePoint >= 10;
      },
      clickableFront2() {
        return this.currentBasePoint >= 10;
      },
      clickableFront3() {
        return this.currentBasePoint >= 10;
      },
      clickableFront4() {
        return this.currentBasePoint >= 10;
      },
      clickableFront5() {
        return this.currentBasePoint >= 10;
      },
      clickableFront6() {
        return this.currentBasePoint >= 10;
      },
      clickableFront7() {
        return this.currentBasePoint >= 10;
      },
      clickableFront8() {
        return this.currentBasePoint >= 10;
      },
      clickableFront9() {
        return this.currentBasePoint >= 10;
      },
      clickableFront10() {
        return this.currentBasePoint >= 10;
      },
    }
  }
</script>

<style lang="scss" scoped>
  .skill-container {
    width: 1200px; // 固定にするしかなかろう
    min-width: 1200px;
  }

  #base-skilltree {
    position: relative;
    width: 100%;
    height: 150px;
    border: double 10px black;
    -webkit-border-radius: 30px;
    -moz-border-radius: 30px;
    border-radius: 30px;

    #base-inner {
      position: absolute;
      width: 100%;
      height: 100%;


      padding-top: 30px;

      -webkit-border-radius: 20px;
      -moz-border-radius: 20px;
      border-radius: 20px;
    }

    #base-skilltree-title {
      color: yellow;
      -webkit-text-stroke: 2px black;
      text-stroke: 2px black;
      font-weight: 900;
      font-size: 50px;

      position: absolute;
      bottom: -50px;
      right: 45%;
      z-index: 1;
    }
  }

  .skilltree {
    position: relative;
    height: 1400px;
    width: 500px;
    -webkit-border-top-left-radius: 40px;
    -webkit-border-bottom-right-radius: 40px;
    -moz-border-radius-topleft: 40px;
    -moz-border-radius-bottomright: 40px;
    border-top-left-radius: 40px;
    border-bottom-right-radius: 40px;
    border: double 10px black;
  }

  .inner-skilltree {
    position: absolute;
    height: 100%;
    width: calc(100%);
    background-color: #7f828b;
    -webkit-border-top-left-radius: 35px;
    -webkit-border-bottom-right-radius: 35px;
    -moz-border-radius-topleft: 29px;
    -moz-border-radius-bottomright: 29px;
    border-top-left-radius: 29px;
    border-bottom-right-radius: 29px;
  }

  #frontend-tree {
    background-color: lightgrey;
  }

  #frontend-skilltree-title {
    color: lawngreen;
    -webkit-text-stroke: 2px black;
    text-stroke: 2px black;
    font-weight: 900;
    font-size: 50px;

    position: absolute;
    bottom: -50px;
    z-index: 1;
  }

  #backend-tree {
    background-color: lightgrey;
  }

  #devops-tree {
    background-color: lightgrey;
  }

  .skill-dialog-card {
    border: double 10px black;
    -webkit-border-radius: 30px;
    -moz-border-radius: 30px;
    border-radius: 30px;
  }

</style>
