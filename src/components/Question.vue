<template lang="pug">
  .question(v-if="show" style=`background-image: url(${imgBackground})`)
    .layout
      h2 Где был сделан это снимок?
      button(@click="reply(1)") {{ answerOne }}
      button(@click="reply(2)") {{ answerTwo }}     
</template>

<script>
export default {
  name: 'question',
  data() {
    return {
      imgBackground: './../assets/2.png',
    };
  },
  props: [
    'answerOne',
    'answerTwo',
    'show',
    'true',
    'img',
  ],
  methods: {
    reply(answer) {
      if (answer === 1 && this.true === 1) {
        console.log('Правильный ответ: ', this.answerOne);
      } else if (answer === 2 && this.true === 2) {
        console.log('Правильный ответ: ', this.answerTwo);
      } else {
        console.log('А вот и не правильно, лох');
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus">
  .question 
    position absolute
    top 0
    left 0
    right 0
    bottom 0
    background-image url('./../assets/2.png')
    background-size cover
    background-position center
    h2 
      color #fff
</style>
