<template>
    <div class="home">
      <home-header></home-header>
      <div class="message-body">
       <home-message v-for="(item,index) in dataList" :key="index" :message="item"></home-message>
      </div>
      <home-input></home-input>
    </div>
</template>

<script>
import HomeHeader from './components/header'
import HomeMessage from './components/message'
import axios from 'axios'
import HomeInput from './components/input'

export default {
  name: 'home',
  components: {
    HomeInput,
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
      let lastTime
      let lastName
      this.dataList.forEach((ele) => {
        if (ele.name === 'Me') {
          ele.isLeft = false
        } else {
          ele.isLeft = true
        }
        ele.time = this.stampToDate(ele.time)
        if (lastTime) {
          ele.lastTime = lastTime
        }
        lastTime = ele.time
        if (ele.lastTime) {
          const timeShow = this.ifTimeShow(ele.lastTime, ele.time)
          ele.timeShow = timeShow
        } else {
          ele.timeShow = true
        }
        if (lastName) {
          ele.lastName = lastName
        }
        lastName = ele.name
        if (ele.lastName) {
          if (ele.lastName === ele.name) {
            ele.infoShow = false
          } else ele.infoShow = true
        } else {
          ele.infoShow = true
        }
      })
      console.log(this.dataList)
    },
    ifTimeShow (sta, en) {
      let start = new Date(sta)
      let end = new Date(en)
      let s = end.getTime() - start.getTime()
      let ss = s / 60000
      if (ss > 5) { return true } else { return false }
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
  .home
    background :#eee
    position: absolute
    bottom :0
    top:0
    left:0
    right :0
    .message-body
      padding-bottom :1rem
      padding-top : .92rem
      align-items :center
      width :100%
</style>
