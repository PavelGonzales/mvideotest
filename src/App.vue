<template>
  <div id="app">
    <img class="app_logo" src="./assets/logo.png">
    <hello v-if="!started" 
           @start="next"></hello>
    <question v-for="question in questions" 
              :answerOne=question.answerOne
              :answerTwo=question.answerTwo
              :true=question.true
              :img=question.img
              :show="question.show"
              :key="question.id"
              @right="pushAnswer"
              @next="next"></question>
    <done :title="winnerTitle"
          :text="winnerText"
          :right="right"
          :length="this.questions.length"></done>
  </div>
</template>

<script>
import Hello from './components/Hello';
import Question from './components/Question';
import Done from './components/Done';

export default {
  name: 'app',
  data() {
    return {
      counter: 0,
      right: 0,
      done: false,
      started: false,
      winnerTitle: null,
      winnerText: null,
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
        {
          answerOne: 'Барселона, Испания',
          answerTwo: 'Аляска, Россия',
          true: 2,
          img: '3',
          show: false,
        },
        {
          answerOne: 'Барселона, Испания',
          answerTwo: 'Аляска, Россия',
          true: 2,
          img: '3',
          show: false,
        },
        {
          answerOne: 'Барселона, Испания',
          answerTwo: 'Аляска, Россия',
          true: 2,
          img: '3',
          show: false,
        },
        {
          answerOne: 'Барселона, Испания',
          answerTwo: 'Аляска, Россия',
          true: 2,
          img: '3',
          show: false,
        },
        {
          answerOne: 'Барселона, Испания',
          answerTwo: 'Аляска, Россия',
          true: 2,
          img: '3',
          show: false,
        },
        {
          answerOne: 'Барселона, Испания',
          answerTwo: 'Аляска, Россия',
          true: 2,
          img: '3',
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
    Done,
  },
  methods: {
    setWinnerText() {
      if (this.right >= 0 && this.right <= 2) {
        this.winnerTitle = 'Любитель конкурных карт';
        this.winnerText = 'Ох, видимо, о разнообразии природы России вы знаете только по контурным картам. Не отчаивайтесь, мы знаем как вам помочь! Для того, чтобы узнать о красоте России, нужно всего лишь захотеть этого и прийти на выставку «100 заповедных лет» Игоря Шпиленика __ _____ 2017.';
      }
      if (this.right >= 3 && this.right <= 4) {
        this.winnerTitle = 'На грани фола';
        this.winnerText = 'Здорово, что первая ассоциация с Байкалом для вас не лимонад, но вот Курильские острова от Канарских вы едва сможете отличить. Мы никому об этом не расскажем, даже выход подскажем, как знания быстро прокачать. Приходите на выставку «100 заповедных лет» Игоря Шпиленика __ ____ 2017, открывайте для себя заповедную природу России во всей ее захватывающей красоте.';
      }
      if (this.right >= 5 && this.right <= 6) {
        this.winnerTitle = 'Профессионал инста-серфинга!';
        this.winnerText = 'Понимаем, у вас очень много дел! Так много, что разнообразие природы России вы видите только тогда, когда пролистываете фотографии друзей в социальных сетях. Сейчас самое время исправиться и узнать, что в России есть что-то кроме Сочи, где жаркие ночи, Питера и «нашего» Крыма. Приходите на выставку «100 заповедных лет» Игоря Шпиленика __ _____ 2017, открывайте для себя заповедную природу России во всей ее поражающей красоте.';
      }
      if (this.right >= 7 && this.right <= 8) {
        this.winnerTitle = 'Зам главного Географа всея Руси';
        this.winnerText = 'Отличный результат, можно смело хвастаться друзьям! Вы отлично чувствуете границы, но все же, для вас есть что-то неизвестное. И это хорошо, значит природе России есть, чем вас удивить! Для прокачки знаний мы приглашаем вас на выставку «100 заповедных лет» Игоря Шпиленика __ _____ 2017, где мы покажем то, от чего у вас, наверняка, захватит дух!';
      }
      if (this.right >= 9 && this.right <= 10) {
        this.winnerTitle = 'Поздравляем, вы Географ всея Руси';
        this.winnerText = 'Вот это да! Вы настолько круто знаете заповедную природу России, что сам ведущий программы «Вокруг Света» вам завидует. Не смотря на все ваши королевские знания, вам будет любопытно заглянуть на выставку «100 заповедных лет» Игоря Шпиленика. Наверняка вы найдете что-то интересное и неизведанное для себя.';
      }
    },
    pushAnswer() {
      this.right = this.right + 1;
    },
    next() {
      this.started = true;
      if (this.counter >= this.questions.length) {
        this.done = true;
        this.questions[this.counter - 1].show = false;
        this.setWinnerText();
        return;
      }
      if (this.counter !== 0) {
        this.questions[this.counter - 1].show = false;
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
  height 100%
  margin auto
  display flex 
  justify-content center
  align-items center
  flex-direction column
  text-align center
</style>
