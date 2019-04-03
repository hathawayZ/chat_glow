<template>
    <div>
      <home-header></home-header>
      <home-message></home-message>
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
  methods: {
    getHomeInfo () {
      axios.get('/api/fe-chat-test.json').then(this.getHomeInfoSuc)
    },
    getHomeInfoSuc (res) {
      console.log(res)
    }
  },
  mounted () {
    this.getHomeInfo()
  }
}
</script>

<style lang="stylus" scoped>

</style>
