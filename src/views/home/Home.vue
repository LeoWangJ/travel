<template>
  <div>
    <home-header></home-header>
    <swiper :list="swiperList"></swiper>
    <icons :list="iconList"></icons>
    <recommand :list="recommendList"></recommand>
    <weekend :list="weekendList"></weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import Swiper from './components/Swiper'
import Icons from './components/Icons'
import Recommand from './components/Recommand'
import Weekend from './components/Weekend'
import axios from 'axios'
import { mapState } from 'vuex'

export default {
  name: 'home',
  components: {
    HomeHeader,
    Swiper,
    Icons,
    Recommand,
    Weekend
  },
  data () {
    return {
      iconList: [],
      recommendList: [],
      swiperList: [],
      weekendList: [],
      lastCity: ''
    }
  },
  mounted () {
    this.lastCity = this.city
    this.getHomeInfo()
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.getHomeInfoSuccess)
    },
    getHomeInfoSuccess (res) {
      res = res.data

      if (res.ret && res.data) {
        let data = res.data
        this.iconList = data.iconList
        this.recommendList = data.recommendList
        this.swiperList = data.swiperList
        this.weekendList = data.weekendList
      }
    }
  },
  activated () {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
