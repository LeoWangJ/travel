<template>
    <div>
        <div class="search">
            <input type="text" class="search-input" placeholder="輸入城市名或拼音" v-model="keyword" />
        </div>
        <div class="search-content" ref="search" v-show="keyword">
            <ul>
                <li class="search-item border-bottom" v-for="item of list" :key="item.id" @click="handleCityClick(item.name)">{{item.name}}</li>
                <li class="search-item border-bottom" v-show="hasNoData">沒有找到相關數據</li>
            </ul>
        </div>
    </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapMutations } from 'vuex'

export default {
  name: 'citySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  computed: {
    hasNoData () {
      return !this.list.length
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let item in this.cities) {
          this.cities[item].forEach(innerItem => {
            if (innerItem.spell.indexOf(this.keyword) > -1 || innerItem.name.indexOf(this.keyword) > -1) {
              result.push(innerItem)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.search)
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
      this.keyword = ''
      this.list = []
    },
    ...mapMutations(['changeCity'])
  }
}
</script>

<style lang="scss" scoped>
    @import '~styles/varibles.scss';
    .search{
        height: .72rem;
        background: $bgColor;
        padding: 0 .1rem;
        &-input{
            height: .62rem;
            line-height: .62rem;
            width: 100%;
            border-radius: .06rem;
            text-align: center;
            color:#666;
            padding: 0 .1rem;
            box-sizing: border-box;
        }
    }
    .search-content{
        position: absolute;
        top: 1.58rem;
        left: 0;
        right: 0;
        bottom: 0;
        overflow: hidden;
        z-index: 1;
        background: #eee;
        .search-item{
          line-height: .62rem;
          padding-left:.2rem;
          color:#666;
          background: #fff;
        }
    }
</style>
