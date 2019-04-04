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
      console.log(data)
      for (let x in data) {
        this.dataList.push(data[x])
      }
      this.dataList.forEach((ele) => {
        if (ele.name === 'Me') {
          ele.isLeft = false
        } else {
          ele.isLeft = true
        }
        ele.time = this.stampToDate(ele.time)
      })
      // console.log(this.dataList)
    },
    stampToDate (res) {
      const date = new Date(parseInt(res * 1000))
      // console.log(date)
      const year = date.getFullYear()
      const month = (date.getMonth() + 1 < 10 ? '0' + (date.getMonth() + 1) : date.getMonth() + 1)
      const day = date.getDate()
      const hour = date.getHours() < 10 ? '0' + date.getHours() : date.getHours()
      const minute = date.getMinutes() < 10 ? '0' + date.getMinutes() : date.getMinutes()
      return year + '-' + month + '-' + day + ' ' + hour + ':' + minute
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
