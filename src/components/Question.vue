<template lang="pug">
  .question(v-if="show")
    .layout
      img(:src="this.getImgUrl")
      .question__content
        h2 Где был сделан это снимок?
        button(@click="reply(1)") {{ answerOne }}
        button(@click="reply(2)") {{ answerTwo }}     
</template>

<script>
export default {
  name: 'question',
  computed: {
    getImgUrl() {
      const image = require.context('../assets/', false, /\.png$/);
      return image(`./${this.img}.png`);
    },
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
        this.$emit('wrong');
      }
      this.$emit('next');
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
    &__content 
      position relative
    img
      position absolute
      top 0
      left 0
      width 100%
      height 100%
      object-fit cover
    h2 
      color #fff
</style>
