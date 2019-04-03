<template>
  <div class="header">
    <div class="header-title">
      聊天室
    </div>
  </div>
</template>

<script>
export default {
  name: 'homeHeader'
}
</script>

<style lang="stylus" scoped>
  .header
    line-height:1.26rem
    z-index: 5
    position:fixed
    width :100%
    display :flex
    background :#00bcd4
    color:#fff
  .header-title
    flex:1
    color :#ff
    height :.92rem
    line-height :.92rem
    text-align :center
    font-size :.62rem
</style>
