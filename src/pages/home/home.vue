<template>
    <div>
      <home-header></home-header>
      <div class="message-body">
       <home-message v-for="(item,index) in dataList" :key="index" :message="item"></home-message>
      </div>
    </div>
</template>

<script>
import HomeHeader from './components/header'
import HomeMessage from './components/message'
import axios from 'axios'

export default {
  name: 'home',
  components: {
    HomeMessage,
    HomeHeader},
  data () {
    return {
      dataList: []
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/fe-chat-test.json').then(this.getHomeInfoSuc)
    },
    getHomeInfoSuc (res) {
      const data = res.data
      // console.log(data)
      for (let x in data) {
        this.dataList.push(data[x])
      }
      this.dataList.forEach((ele) => {
        if (ele.name === 'Me') {
          ele.isLeft = false
        } else {
          ele.isLeft = true
        }
      })
      console.log(this.dataList)
    }
  },
  mounted () {
    this.getHomeInfo()
  }
}
</script>

<style lang="stylus" scoped>
  .message-body
    padding-top : .92rem
    align-items :center
    background :#eee
    width :100%
</style>
