<template>
      <div class="message-body">
        <div class="user" v-if="isLeft">
          <div class="info">
            <div class="name">wyz</div>
            <div class="avatar">
              <img class="avatar-img" src="https://bpic.588ku.com/original_origin_min_pic/18/11/26/b39b42668b8137bdd18fe49d7ffe3a3e.jpg">
            </div>
          </div>
          <div class="message-wrapper">
            <div class="item-wrapper">
              <div class="wrapper-item">
                wyz最喜欢zmm啦~！
              </div>
            </div>
          </div>
        </div>
        <div class="user" v-if="!isLeft">
          <div class="message-wrapper">
            <div class="item-wrapper1">
              <div class="wrapper-item">
                wyz最喜欢zmm啦~！
              </div>
            </div>
          </div>
          <div class="info">
            <div class="name">wyz</div>
            <div class="avatar1">
              <img class="avatar-img" src="https://bpic.588ku.com/original_origin_min_pic/18/11/26/b39b42668b8137bdd18fe49d7ffe3a3e.jpg">
            </div>
          </div>
        </div>
      </div>
</template>

<script>
export default {
  name: 'HomeMessage',
  data () {
    return {
      isLeft: false
    }
  }
}
</script>

<style lang="stylus" scoped>
.message-body
  align-items :center
  background :#eee
  width :100%
  padding-bottom :90%
  .user
    display :flex
    overflow:hidden
    box-sizing :border-box
    padding-top :.2rem
    padding-left:.2rem
    padding-right :.2rem
    .info
      flex :1
      .name
        padding-bottom :.1rem
        color :#999
      .avatar
        float :left
        height :1.5rem
        width :1.5rem
        .avatar-img
          width :100%
          height :100%
          border-radius :.2rem
      .avatar1
        float :right
        height :1.5rem
        width :1.5rem
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
        top:.6rem
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
        top:.6rem
        right:.1rem
        .wrapper-item
          line-height :.8rem
          height :.8rem
          margin: 0 .1rem 0 0.2rem
</style>
