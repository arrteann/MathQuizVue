<template>
  <div id="app">
    <app-header></app-header>
    <div id="container">
      <app-selector
        v-if="!operator"
        @changeoperator="changeoperator"
      ></app-selector>
      <app-quiz
        v-if="this.operator"
        @onback="clear"
        :operator="this.operator"
      ></app-quiz>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Selector from "./components/Operatorselector";
import Quiz from "./components/OperatorQuiz";
export default {
  name: "App",
  data() {
    return {
      operator: null,
    };
  },
  components: {
    appHeader: Header,
    appSelector: Selector,
    appQuiz: Quiz,
  },
  methods: {
    changeoperator(operator) {
      this.operator = operator;
      console.log(operator);
    },
    clear() {
      this.operator = null;
    },
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#container {
  width: 50rem;
  margin: 4rem auto 0rem;
  padding: 40px;
  box-shadow: 0px 3px 6px rgba($color: #000000, $alpha: 0.2);
}
</style>
