<template>
    <div class="input">
      <el-input
        type="textarea"
        :autosize="{ minRows: 1, maxRows: 4}"
        placeholder="请输入内容"
        v-model="text"
        clearable
        class="input-text">
      </el-input>
      <el-button type="primary" class="send" size ='medium' @click="sendMsg">发送</el-button>
    </div>
</template>

<script>
export default {
  name: 'homeInput',
  data () {
    return {
      text: ''
    }
  },
  methods: {
    sendMsg () {
      this.$emit('sendmsg', this.text)
      this.text = ''
    }
  }
}
</script>

<style lang="stylus" scoped>
.input
  z-index :5
  position :fixed
  bottom :0
  right :0
  left:0
  display :flex
  .input-text
    flex:7
  .send
    flex :1
    flex-grow :0
</style>
