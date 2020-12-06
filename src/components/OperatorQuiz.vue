<template>
  <div>
    <div v-if="isQuizStarted">
      <h1>
        {{ this.operandLeft }} {{ this.operator }} {{ this.operandRight }}
      </h1>

      <div>
        <span
          v-for="(answer, index) of answers"
          :key="index"
          @click="selectAnswer(answer)"
        >
          {{ answer }}
        </span>
      </div>
      <span @click="$emit('onback')">BACK</span>
    </div>
    <div v-if="!isQuizStarted">
      <span @click="startQuiz">START</span>
      <span @click="$emit('onback')">BACK</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Quiz",
  props: ["operator"],
  data() {
    return {
      isQuizStarted: false,
      operandLeft: null,
      operandRight: null,
      answers: [],
      execptedAnswer: null,
    };
  },
  methods: {
    selectAnswer(answer) {
      if (answer !== this.execptedAnswer) {
        alert("WRONG ANSWER");
      }
      this.startQuiz();
    },
    startQuiz() {
      this.isQuizStarted = true;
      this.operandLeft = parseInt(Math.random() * 13);
      this.operandRight = parseInt(Math.random() * 13);

      const method = {
        "+": (a, b) => a + b,
        "-": (a, b) => a - b,
        "/": (a, b) => a / b,
        "*": (a, b) => a * b,
      };

      const methodToUse = method[this.operator];

      this.answers = [];
      this.answers.push(methodToUse(this.operandLeft, this.operandRight + 1));
      this.answers.push(methodToUse(this.operandLeft + 1, this.operandRight));
      this.answers.push(
        methodToUse(this.operandLeft + 1, this.operandRight + 1)
      );
      this.answers.push(
        methodToUse(this.operandLeft - 1, this.operandRight + 1)
      );
      this.answers.push(methodToUse(this.operandLeft, this.operandRight - 1));

      const execptedAnswer = methodToUse(this.operandLeft, this.operandRight);

      this.answers[
        parseInt(Math.random() * this.answers.length)
      ] = execptedAnswer;
      this.execptedAnswer = execptedAnswer;
    },
  },
};
</script>

<style lang="scss" scoped>
</style>