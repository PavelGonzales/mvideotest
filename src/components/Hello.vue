<template lang="pug">
  .hello
    .layout
      h1 Россия или не Россия?
      p Сможете	ли	вы	узнать	заповедные	места	нашей	<br>страны	по	фотографии?	<br><br>М.Видео	предлагает	пройти	этот	тест,	в	котором	<br>собраны	реальные	и	вымышленные	места	<br>и	узнать,	насколько	легко	вас	обвести	<br>вокруг	пальца.
      button начать
</template>

<script>
export default {
  name: 'hello',
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus">
  .hello 
    position absolute
    top 0
    left 0
    right 0
    bottom 0
    background-image url('./../assets/1.png')
    background-size cover
    background-position center
</style>
