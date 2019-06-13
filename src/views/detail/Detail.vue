<template>
    <div>
        <banner :sightName="sightName" :bannerImg="bannerImg" :gallaryImgs="gallaryImgs"></banner>
        <detail-header></detail-header>
        <div class="content">
          <detail-list :list="categoryList" ></detail-list>
        </div>
    </div>
</template>

<script>
import Banner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'

export default {
  name: 'detail',
  components: {
    Banner,
    DetailHeader,
    DetailList
  },
  data () {
    return {
      bannerImg: '',
      categoryList: [],
      gallaryImgs: [],
      sightName: ''
    }
  },
  mounted () {
    this.getDetailInfo()
  },
  methods: {
    getDetailInfo () {
      axios.get('/api/detail.json', {
        params: {
          id: this.$route.params.id
        }
      })
        .then(this.handleDetailInfoSuccess)
        .catch(err => {
          console.log(err)
        })
    },
    handleDetailInfoSuccess (res) {
      res = res.data
      console.log(res.data)
      if (res.ret && res.data) {
        let data = res.data
        this.bannerImg = data.bannerImg
        this.categoryList = data.categoryList
        this.gallaryImgs = data.gallaryImgs
        this.sightName = data.sightName
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .content{
      height: 50rem;
  }
</style>
