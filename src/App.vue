<template>
  <div id="app">
    <img class="app_logo" src="./assets/logo.png">
    <hello @start="next"></hello>
    <question v-for="question in questions" 
              :answerOne=question.answerOne
              :answerTwo=question.answerTwo
              :true=question.true
              :img=question.img
              :show="question.show"
              @wrong="pushAnswer"
              @next="next"></question>
  </div>
</template>

<script>
import Hello from './components/Hello';
import Question from './components/Question';

export default {
  name: 'app',
  data() {
    return {
      counter: 0,
      wrong: 0,
      questions: [
        {
          answerOne: 'Сочи, Россия',
          answerTwo: 'Торро, Испания',
          true: 1,
          img: '1',
          show: false,
        },
        {
          answerOne: 'Крым, Россия',
          answerTwo: 'Кентуки',
          true: 1,
          img: '2',
          show: false,
        },
        {
          answerOne: 'Барселона, Испания',
          answerTwo: 'Аляска, Россия',
          true: 2,
          img: '3',
          show: false,
        },
      ],
    };
  },
  components: {
    Hello,
    Question,
  },
  methods: {
    pushAnswer() {
      this.wrong = this.wrong + 1;
    },
    next() {
      if (this.counter >= this.questions.length) {
        console.log(this.questions.length - this.wrong, '/', this.questions.length);
        return;
      }
      this.questions[this.counter].show = true;
      this.counter = this.counter + 1;
    },
  },
};
</script>

<style lang="stylus">
body
html 
  margin 0
  padding 0
#app 
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  position absolute
  top 0
  left 0
  width 100%
  min-height 100vh

.app_logo
  position absolute
  top 50px
  right 50px
  z-index 10

.layout
  width 960px
  margin auto
</style>
