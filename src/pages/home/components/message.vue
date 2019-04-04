<template>
  <div>
        <div class="time" v-if="message.timeShow">
          {{message.time}}
        </div>
        <div class="user" v-if="message.isLeft">
          <div class="info" >
            <div class="name">
              <div v-show="message.infoShow">
                {{message.name}}
              </div>
            </div>
            <div class="avatar">
              <img class="avatar-img" :src="message.avatar">
            </div>
          </div>
          <div class="message-wrapper">
            <div class="item-wrapper">
              <div class="wrapper-item">
                {{message.text}}
              </div>
            </div>
          </div>
        </div>
        <div class="user" v-if="!message.isLeft">
          <div class="message-wrapper">
            <div class="item-wrapper1">
              <div class="wrapper-item">
                {{message.text}}
              </div>
            </div>
          </div>
          <div class="info" >
            <div class="name1" >
              <div v-show="message.infoShow" >
              {{message.name}}
              </div>
            </div>
            <div class="avatar1" >
              <img class="avatar-img" src="https://bpic.588ku.com/original_origin_min_pic/18/11/26/b39b42668b8137bdd18fe49d7ffe3a3e.jpg" v-if="message.infoShow">
            </div>
          </div>
        </div>
  </div>
</template>

<script>
export default {
  name: 'HomeMessage',
  props: {
    message: Object
  },
  data () {
    return {
    }
  }
}
</script>

<style lang="stylus" scoped>
  .time
    text-align :center
    color :#888
    font-size :.24rem
    padding-top:.2rem
  .user
    display :flex
    overflow:hidden
    box-sizing :border-box
    padding-bottom :.2rem
    padding-left:.2rem
    padding-right :.2rem
    .info
      flex :1
      flex-grow :0
      .name
        padding-bottom :.2rem
        height :0
        color :#999
      .name1
        padding-bottom :.2rem
        height :0
        text-align :right
        color :#999
      .avatar
        margin-top :.1rem
        float :left
        height :1rem
        width :1rem
        .avatar-img
          width :100%
          height :100%
          border-radius :.2rem
      .avatar1
        margin-top :.1rem
        float :right
        height :1rem
        width :1rem
        .avatar-img
          width :100%
          height :100%
          border-radius :.2rem
    .message-wrapper
      flex:3
      position :relative
      .item-wrapper
        position:absolute
        background :#cacaca
        border :solid .01rem gray
        border-radius :.4rem
        top:.4rem
        left:.1rem
        .wrapper-item
          line-height :.8rem
          height :.8rem
          margin: 0 .2rem
      .item-wrapper1
        position:absolute
        background : #bedde7
        border :solid .01rem #9ab1bb
        border-radius :.4rem
        top:.4rem
        right:.1rem
        .wrapper-item
          line-height :.8rem
          height :.8rem
          margin: 0 .1rem 0 0.2rem
</style>
