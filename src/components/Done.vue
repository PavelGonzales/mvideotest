<template lang="pug">
  .done
    .layout
      .done__content
        h2 {{ this.title }}
        p {{ this.text }}
        span {{ this.right }} / {{ this.length }}
        .social_buttons
          button(@click="share.fb()") fb
          button(@click="share.vk()") vk    
          button(@click="share.ok()") ok      
</template>

<script>
export default {
  name: 'done',
  props: [
    'done',
    'right',
    'length',
    'title',
    'text',
  ],
  methods: {
    share: {
      fb() {
        console.log('share fb');
      },
      vk() {
        console.log('share vk');
      },
      ok() {
        console.log('share ok');
      },
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus">
  .done 
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
    p 
      color #fff
    span 
      color #fff
      font-size 24px
</style>
