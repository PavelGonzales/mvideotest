<template lang="pug">
  .done
    .layout
      .done__content
        h2 {{ this.title }}
        p {{ this.text }}
        span {{ this.right }} / {{ this.length }}
        .social_buttons
          button(@click="fb('URL','TITLE','IMG_PATH','DESC')") fb
          button(@click="vk('URL','TITLE','https://media.licdn.com/media/p/8/000/1e9/0e5/26e178f.png','DESC')") vk    
          button(@click="ok('URL','DESC')") ok      
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
    fb() {
      console.log('share fb');
    },
    vk(purl, ptitle, pimg, text) {
      let url = 'http://vkontakte.ru/share.php?';
      url += `url=${encodeURIComponent(purl)}`;
      url += `&title=${encodeURIComponent(ptitle)}`;
      url += `&description=${encodeURIComponent(text)}`;
      url += `&image=${encodeURIComponent(pimg)}`;
      url += '&noparse=true';
      this.popup(url);
      console.log('share vk');
    },
    ok() {
      console.log('share ok');
    },
    popup(url) {
      window.open(url, '', 'toolbar=0,status=0,width=626,height=436');
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
