<template lang="pug">
  v-layout(column justify-center align-center)
    div.skill-container.mb-5
      // base-skilltree
      div#base-skilltree.mb-5(:style="baseSkillTreeStyle")
        div#base-inner.px-2.pt-3(:style="baseSkillTreeInnerStyle")
          h1#base-skilltree-title BASE {{currentBasePoint}}
          v-layout(row justify-space-between)
            git(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            basic-terminal-usage(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            data-structure(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            solid(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            git-hub(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            license(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            semantic-versioning(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            s-s-h(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            http-api(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            design-pattern(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
            character-encoding(v-on:set-skill-points="setCurrentSkillPoint" :clickable="true")
      v-layout(row fluid)
        // front-end tree
        div.skilltree#frontend-tree.mr-3(:style="frontSkillTreeStyle")
          div.inner-skilltree.px-2.pt-3(:style="frontSkillTreeInnerStyle")
            h1#frontend-skilltree-title FRONTEND {{currentFrontPoint}}
            // 第1階層
            v-layout.mb-3(row justify-space-between)
              html-skill(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront1")
              css-skill(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront1")
              javascript(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront1")
            // 第2階層
            v-layout.mb-3(row justify-center)
              package-manager(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront2")
            // 第3階層
            v-layout.mb-3(row justify-space-between)
              css-preprocessor(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront3")
              css-framework(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront3")
              css-architecture(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront3")
            // 第4階層
            v-layout.mb-3(row justify-space-between)
              linter(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront4")
              module-bundler(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront4")
              task-runner(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront4")
            // 第5階層
            v-layout.mb-3(row justify-space-between)
              react(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront5")
              angular(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront5")
              vue-skill(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront5")
            // 第6階層
            v-layout.mb-3(row justify-space-between)
              css-in-js(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront6")
              test(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront6")
            // 第7階層
            v-layout.mb-3(row justify-center)
              type-checker(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront7")
            // 第8階層
            v-layout.mb-3(row justify-space-between)
              pwa(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront8")
              ssr(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront8")
            // 第9階層
            v-layout.mb-3(row justify-space-between)
              static-site-generator(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront9")
              mobile(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront9")
              desktop(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront9")
            // 第10階層
            v-layout.mb-3(row justify-center)
              web-assembly(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableFront10")

        // back-end tree
        div.skilltree#backend-tree.mr-3(:style="backSkillTreeStyle")
          div.inner-skilltree.px-2.pt-3(:style="backSkillTreeInnerStyle")
            h1#backend-skilltree-title BACKEND {{currentBackendPoint}}
            // 第1階層(言語一覧)
            v-layout.mb-3(row justify-space-between)
              python(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              ruby-skill(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              php(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              node(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
            // 第1階層(言語一覧)
            v-layout.mb-3(row justify-space-between)
              elixir(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              scala(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              erlang(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              clojure(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              haskell(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
            // 第1階層(言語一覧)
            v-layout.mb-3(row justify-space-between)
              golang(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              rust(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              java(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
              n-e-t(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack1")
            // 第2階層
            v-layout.mb-3(row justify-space-between)
              command-line-application(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack2")
              backend-package-manager(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack2")
              standard-and-best-practice(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack2")
            // 第3階層
            v-layout.mb-3(row justify-space-between)
              make-package-or-library(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack3")
              backend-testing(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack3")
              test-for-practical-step(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack3")
            // 第4階層
            v-layout.mb-3(row justify-space-between)
              relational-database(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack4")
              basic-crud(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack4")
            // 第5階層
            v-layout.mb-3(row justify-center)
              framework(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack5")
            // 第6階層
            v-layout.mb-3(row justify-space-between)
              no-sql(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack6")
              caching(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack6")
              create-r-e-s-t-ful-a-p-i(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack6")
            // 第7階層
            v-layout.mb-3(row justify-space-between)
              authentication(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack7")
              message-brokers(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack7")
              search-engine(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack7")
            // 第8階層
            v-layout.mb-3(row justify-space-between)
              docker(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack8")
              web-server(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack8")
              web-socket(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack8")
            // 第9階層
            v-layout.mb-3(row justify-space-between)
              graph-q-l(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack9")
              graph-database(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack9")
            // 第10階層
            v-layout.mb-3(row justify-center)
              more(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableBack10")

        // dev-ops tree
        div.skilltree#devops-tree.mr-3(:style="devopsSkillTreeStyle")
          div.inner-skilltree.px-2.pt-3(:style="devopsSkillTreeInnerStyle")
            h1#devops-skilltree-title DEVOPS {{currentDevopsPoint}}
            // 第1階層(言語一覧)
            v-layout.mb-3(row justify-space-between)
              dev-python(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops1")
              dev-ruby-skill(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops1")
              dev-node(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops1")
            // 第1階層(言語一覧)
            v-layout.mb-3(row justify-space-between)
              dev-golang(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops1")
              dev-rust(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops1")
              cplusplus(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops1")
            // 第2階層
            v-layout.mb-3(row justify-center)
              o-s-concept(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops2")
            // 第3階層
            v-layout.mb-3(row justify-space-between)
              managing-server-o-s(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops3")
              managing-server-terminal(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops3")
            // 第4階層
            v-layout.mb-3(row justify-space-between)
              network-and-security(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops4")
              firewall(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops4")
              setup-webserver(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops4")
            // 第5階層
            v-layout.mb-3(row justify-space-between)
              container(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops5")
              configuration-management(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops5")
              container-orchestration(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops5")
            // 第6階層
            v-layout.mb-3(row justify-center)
              infra-provisioning(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops6")
            // 第7階層
            v-layout.mb-3(row justify-center)
              c-i-c-d(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops7")
            // 第8階層
            v-layout.mb-3(row justify-space-between)
              infrast-monitoring(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops8")
              application-monitoring(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops8")
              log-management(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops8")
            // 第9階層
            v-layout.mb-3(row justify-center)
              cloud-provider(v-on:set-skill-points="setCurrentSkillPoint" :clickable="clickableDevops9")


</template>

<script>
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
  import CssInJs from '~/components/frontend-skills/CssInJs';
  import Test from '~/components/frontend-skills/Test';
  import Pwa from '~/components/frontend-skills/Pwa';
  import TypeChecker from '~/components/frontend-skills/TypeChecker';
  import Ssr from '~/components/frontend-skills/Ssr';
  import StaticSiteGenerator from '~/components/frontend-skills/StaticSiteGenerator';
  import Desktop from '~/components/frontend-skills/Desktop';
  import Mobile from '~/components/frontend-skills/Mobile';
  import WebAssembly from '~/components/frontend-skills/WebAssembly';

  // backend
  import Clojure from '~/components/backend-skills/lang/Clojure';
  import Elixir from '~/components/backend-skills/lang/Elixir';
  import Erlang from '~/components/backend-skills/lang/Erlang';
  import Golang from '~/components/backend-skills/lang/Golang';
  import Haskell from '~/components/backend-skills/lang/Haskell';
  import Java from '~/components/backend-skills/lang/Java';
  import NET from '~/components/backend-skills/lang/NET';
  import Node from '~/components/backend-skills/lang/Node';
  import Python from '~/components/backend-skills/lang/Python';
  import Php from '~/components/backend-skills/lang/Php';
  import RubySkill from '~/components/backend-skills/lang/Ruby';
  import Rust from '~/components/backend-skills/lang/Rust';
  import Scala from '~/components/backend-skills/lang/Scala';

  import Authentication from '~/components/backend-skills/Authentication';
  import BasicCrud from '~/components/backend-skills/BasicCrud';
  import Caching from '~/components/backend-skills/Caching';
  import CommandLineApplication from '~/components/backend-skills/CommandLineApplication';
  import CreateRESTFulAPI from '~/components/backend-skills/CreateRESTFulAPI';
  import Docker from '~/components/backend-skills/Docker';
  import Framework from '~/components/backend-skills/Framework';
  import GraphDatabase from '~/components/backend-skills/GraphDatabase';
  import GraphQL from '~/components/backend-skills/GraphQL';
  import MakePackageOrLibrary from '~/components/backend-skills/MakePackageOrLibrary';
  import MessageBrokers from '~/components/backend-skills/MessageBrokers';
  import More from '~/components/backend-skills/More';
  import NoSql from '~/components/backend-skills/NoSql';
  import BackendPackageManager from '~/components/backend-skills/PackageManager';
  import RelationalDatabase from '~/components/backend-skills/RelationalDatabase';
  import SearchEngine from '~/components/backend-skills/SearchEngine';
  import StandardAndBestPractice from '~/components/backend-skills/StandardAndBestPractice';
  import TestForPracticalStep from '~/components/backend-skills/TestForPracticalStep';
  import BackendTesting from '~/components/backend-skills/Testing';
  import WebServer from '~/components/backend-skills/WebServer';
  import WebSocket from '~/components/backend-skills/WebSocket';

  // devops
  import DevPython from '~/components/devops-skills/lang/Python';
  import DevGolang from '~/components/devops-skills/lang/Golang';
  import DevNode from '~/components/devops-skills/lang/Node';
  import DevRubySkill from '~/components/devops-skills/lang/Ruby';
  import DevRust from '~/components/devops-skills/lang/Rust';
  import Cplusplus from '~/components/devops-skills/lang/C++';
  import ApplicationMonitoring from '~/components/devops-skills/ApplicationMonitoring';
  import CICD from '~/components/devops-skills/Cicd';
  import CloudProvider from '~/components/devops-skills/CloudProvider';
  import ConfigurationManagement from '~/components/devops-skills/ConfigurationManagement';
  import Container from '~/components/devops-skills/Container';
  import ContainerOrchestration from '~/components/devops-skills/ContainerOrchestration';
  import Firewall from '~/components/devops-skills/Firewall';
  import InfraProvisioning from '~/components/devops-skills/InfraProvisioning';
  import InfrastMonitoring from '~/components/devops-skills/InfrastMonitoring';
  import LogManagement from '~/components/devops-skills/LogManagement';
  import ManagingServerOS from '~/components/devops-skills/ManagingServerOS';
  import ManagingServerTerminal from '~/components/devops-skills/ManagingServerTerminal';
  import NetworkAndSecurity from '~/components/devops-skills/NetworkAndSecurity';
  import OSConcept from '~/components/devops-skills/OSConcept';
  import SetupWebserver from '~/components/devops-skills/SetupWebserver';

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
      CssInJs,
      Test,
      Pwa,
      TypeChecker,
      Ssr,
      StaticSiteGenerator,
      Desktop,
      Mobile,
      WebAssembly,

      Clojure,
      Elixir,
      Erlang,
      Golang,
      Haskell,
      Java,
      NET,
      Node,
      Php,
      Python,
      RubySkill,
      Rust,
      Scala,

      Authentication,
      BasicCrud,
      Caching,
      CommandLineApplication,
      CreateRESTFulAPI,
      Docker,
      Framework,
      GraphDatabase,
      GraphQL,
      MakePackageOrLibrary,
      MessageBrokers,
      More,
      NoSql,
      BackendPackageManager,
      RelationalDatabase,
      SearchEngine,
      StandardAndBestPractice,
      TestForPracticalStep,
      BackendTesting,
      WebServer,
      WebSocket,

      DevPython,
      DevGolang,
      DevNode,
      DevRubySkill,
      DevRust,
      Cplusplus,
      ApplicationMonitoring,
      CICD,
      CloudProvider,
      ConfigurationManagement,
      Container,
      ContainerOrchestration,
      Firewall,
      InfraProvisioning,
      InfrastMonitoring,
      LogManagement,
      ManagingServerOS,
      ManagingServerTerminal,
      NetworkAndSecurity,
      OSConcept,
      SetupWebserver
    },
    data() {
      return {
        skillDialog: false,

        // それぞれのスキルツリーの基準値
        baseBorder: 10,
        frontendBorder: 30,
        backendBorder: 30,
        devopsBorder: 30,

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
        baseHttpapi: 0,
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

        // backend のそれぞれのポイント
        backClojure: 0,
        backElixir: 0,
        backErlang: 0,
        backGolang: 0,
        backHaskell: 0,
        backJava: 0,
        backNET: 0,
        backNode: 0,
        backPhp: 0,
        backPython: 0,
        backRubySkill: 0,
        backRust: 0,
        backScala: 0,

        backAuthentication: 0,
        backBasicCrud: 0,
        backCaching: 0,
        backCommandLineApplication: 0,
        backCreateRESTFulAPI: 0,
        backDocker: 0,
        backFramework: 0,
        backGraphDatabase: 0,
        backGraphQL: 0,
        backMakePackageOrLibrary: 0,
        backMessageBrokers: 0,
        backMore: 0,
        backNoSql: 0,
        backBackendPackageManager: 0,
        backRelationalDatabase: 0,
        backSearchEngine: 0,
        backStandardAndBestPractice: 0,
        backTestForPracticalStep: 0,
        backBackendTesting: 0,
        backWebServer: 0,
        backWebSocket: 0,

        // devopsのそれぞれのポイント
        devopsNode: 0,
        devopsPython: 0,
        devopsRubySkill: 0,
        devopsRust: 0,
        devopsGolang: 0,
        devopsCplusplus: 0,

        devopsApplicationMonitoring: 0,
        devopsCICD: 0,
        devopsCloudProvider: 0,
        devopsConfigurationManagement: 0,
        devopsContainer: 0,
        devopsContainerOrchestration: 0,
        devopsFirewall: 0,
        devopsInfraProvisioning: 0,
        devopsInfrastMonitoring: 0,
        devopsLogManagement: 0,
        devopsManagingServerOS: 0,
        devopsManagingServerTerminal: 0,
        devopsNetworkAndSecurity: 0,
        devopsOSConcept: 0,
        devopsSetupWebserver: 0,
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
      setCurrentSkillPoint(name, currentPoint) {
        this[name] = currentPoint;
      },
    },

    computed: {
      // base
      currentBasePoint() {
        const sum = this.baseGit + this.baseTerminal + this.baseDataStructure + this.baseSolid + this.baseGithub + this.baseLicense +
                    this.baseSemantic + this.baseSsh + this.baseDesignPattern + this.baseCharacterEncoding + this.baseHttpapi;

        return sum;
      },
      baseSkillTreeStyle() {
        if (this.currentBasePoint < this.baseBorder) {
          return `background-color: lightgrey`;
        } else {
          return `background-color: yellow`;
        }
      },
      baseSkillTreeInnerStyle() {
        const border = (this.currentBasePoint / this.baseBorder) * 100;
        return `background:linear-gradient(180deg,#c7ce00 -30%,#c7ce00 ${border}%,grey ${border}%,grey 150%);`;
      },

      // front
      currentFrontPoint() {
        const sum = this.frontHtml + this.frontCss + this.frontJavascript + this.frontPackageManager + this.frontCssPre + this.frontFramework + this.frontArchitecture + this.frontLinter + this.frontModuleBundler + this.frontTaskRunner + this.frontReact + this.frontAngular + this.frontVue + this.frontTesting + this.frontPwa + this.frontTypechecker + this.frontSsr + this.frontStaticSite + this.frontDesktop + this.frontMobile + this.frontWebAssembly;
        return sum;
      },
      frontSkillTreeStyle() {
        if (this.currentFrontPoint < this.frontendBorder) {
          return `background-color: lightgrey`;
        } else {
          return `background-color: lightgreen`;
        }
      },
      frontSkillTreeInnerStyle() {
        const border = (this.currentFrontPoint / this.frontendBorder) * 100;
        return `background:linear-gradient(180deg,green -30%,green ${border}%,grey ${border}%,grey 150%);`;
      },

      // ポイント加算条件
      clickableFront1() {return this.currentBasePoint >= this.baseBorder;},
      clickableFront2() {return this.currentBasePoint >= this.baseBorder && this.currentFrontPoint >= 3 * 1;},
      clickableFront3() {return this.currentBasePoint >= this.baseBorder && this.currentFrontPoint >= 3 * 2;},
      clickableFront4() {return this.currentBasePoint >= this.baseBorder && this.currentFrontPoint >= 3 * 3;},
      clickableFront5() {return this.currentBasePoint >= this.baseBorder && this.currentFrontPoint >= 3 * 4;},
      clickableFront6() {return this.currentBasePoint >= this.baseBorder && this.currentFrontPoint >= 3 * 5;},
      clickableFront7() {return this.currentBasePoint >= this.baseBorder && this.currentFrontPoint >= 3 * 6;},
      clickableFront8() {return this.currentBasePoint >= this.baseBorder && this.currentFrontPoint >= 3 * 7;},
      clickableFront9() {return this.currentBasePoint >= this.baseBorder && this.currentFrontPoint >= 3 * 8;},
      clickableFront10() {return this.currentBasePoint >= this.baseBorder && this.currentFrontPoint >= 3 * 9;},

      // backend
      currentBackendPoint() {
        const sum = this.backClojure + this.backElixir + this.backErlang + this.backHaskell + this.backGolang + this.backHaskell + this.backJava +
                      this.backNET + this.backNode + this.backPhp + this.backPython + this.backRubySkill + this.backRust + this.backScala +
                      this.backAuthentication + this.backBasicCrud + this.backCaching + this.backCommandLineApplication + this.backCreateRESTFulAPI +
                      this.backDocker + this.backFramework + this.backGraphDatabase + this.backGraphQL + this.backMakePackageOrLibrary + this.backMessageBrokers +
                      this.backMore + this.backNoSql + this.backBackendPackageManager + this.backRelationalDatabase + this.backSearchEngine + this.backStandardAndBestPractice +
                      this.backTestForPracticalStep + this.backBackendTesting + this.backWebServer + this.backWebSocket;
        return sum;
      },
      backSkillTreeStyle() {
        if (this.currentBackendPoint < this.backendBorder) {
          return `background-color: lightgrey`;
        } else {
          return `background-color: lightblue`;
        }
      },
      backSkillTreeInnerStyle() {
        const border = (this.currentBackendPoint / this.backendBorder) * 100;
        return `background:linear-gradient(180deg,dodgerblue -30%,dodgerblue ${border}%,grey ${border}%,grey 150%);`;
      },
      // ポイント加算条件
      clickableBack1() {return this.currentBasePoint >= this.baseBorder;},
      clickableBack2() {return this.currentBasePoint >= this.baseBorder && this.currentBackendPoint >= 3 * 1;},
      clickableBack3() {return this.currentBasePoint >= this.baseBorder && this.currentBackendPoint >= 3 * 2;},
      clickableBack4() {return this.currentBasePoint >= this.baseBorder && this.currentBackendPoint >= 3 * 3;},
      clickableBack5() {return this.currentBasePoint >= this.baseBorder && this.currentBackendPoint >= 3 * 4;},
      clickableBack6() {return this.currentBasePoint >= this.baseBorder && this.currentBackendPoint >= 3 * 5;},
      clickableBack7() {return this.currentBasePoint >= this.baseBorder && this.currentBackendPoint >= 3 * 6;},
      clickableBack8() {return this.currentBasePoint >= this.baseBorder && this.currentBackendPoint >= 3 * 7;},
      clickableBack9() {return this.currentBasePoint >= this.baseBorder && this.currentBackendPoint >= 3 * 8;},
      clickableBack10() {return this.currentBasePoint >= this.baseBorder && this.currentBackendPoint >= 3 * 9;},

      // devops
      currentDevopsPoint() {
        const sum = this.devopsNode + this.devopsPython + this.devopsRubySkill + this.devopsRust + this.devopsGolang + this.devopsCplusplus +
                      this.devopsApplicationMonitoring + this.devopsCICD + this.devopsCloudProvider + this.devopsConfigurationManagement +
                      this.devopsContainer + this.devopsContainerOrchestration + this.devopsFirewall + this.devopsInfraProvisioning +
                      this.devopsInfrastMonitoring + this.devopsLogManagement + this.devopsManagingServerOS + this.devopsManagingServerTerminal +
                      this.devopsNetworkAndSecurity + this.devopsOSConcept + this.devopsSetupWebserver;
        return sum;
      },
      devopsSkillTreeStyle() {
        if (this.currentDevopsPoint < this.backendBorder) {
          return `background-color: lightgrey`;
        } else {
          return `background-color: orangered`;
        }
      },
      devopsSkillTreeInnerStyle() {
        const border = (this.currentDevopsPoint / this.backendBorder) * 100;
        return `background:linear-gradient(180deg,red -30%,red ${border}%,grey ${border}%,grey 150%);`;
      },
      // ポイント加算条件
      clickableDevops1() {return this.currentBasePoint >= this.baseBorder;},
      clickableDevops2() {return this.currentBasePoint >= this.baseBorder && this.currentDevopsPoint >= 3 * 1;},
      clickableDevops3() {return this.currentBasePoint >= this.baseBorder && this.currentDevopsPoint >= 3 * 2;},
      clickableDevops4() {return this.currentBasePoint >= this.baseBorder && this.currentDevopsPoint >= 3 * 3;},
      clickableDevops5() {return this.currentBasePoint >= this.baseBorder && this.currentDevopsPoint >= 3 * 4;},
      clickableDevops6() {return this.currentBasePoint >= this.baseBorder && this.currentDevopsPoint >= 3 * 5;},
      clickableDevops7() {return this.currentBasePoint >= this.baseBorder && this.currentDevopsPoint >= 3 * 6;},
      clickableDevops8() {return this.currentBasePoint >= this.baseBorder && this.currentDevopsPoint >= 3 * 7;},
      clickableDevops9() {return this.currentBasePoint >= this.baseBorder && this.currentDevopsPoint >= 3 * 8;},
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
    height: 1320px;
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

  #backend-skilltree-title {
    color: lightblue;
    -webkit-text-stroke: 2px black;
    text-stroke: 2px black;
    font-weight: 900;
    font-size: 50px;

    position: absolute;
    bottom: -50px;
    z-index: 1;
  }

  #devops-skilltree-title {
    color: orangered;
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
