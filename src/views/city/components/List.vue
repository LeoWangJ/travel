<template>
    <div class="list" ref="wrapper">
        <div>
            <div class="area">
                <div class="title border-topbottom">當前城市</div>
                <div class="button-list">
                    <div class="button-wrap">
                        <div class="button">
                        {{this.currentCity}}
                        </div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">熱門城市</div>
                <div class="button-list">
                    <div class="button-wrap" v-for="item of hotCities" :key="item.id" @click="handleCityClick(item.name)">
                        <div class="button" >
                        {{item.name}}
                        </div>
                    </div>
                </div>
            </div>
            <div class="area" v-for="(item ,key) of cities" :key="key" :ref="key">
                <div class="title border-topbottom">{{key}}</div>
                <div class="item-list">
                    <div class="item border-bottom" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">
                        {{innerItem.name}}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'

export default {
  name: 'cityList',
  props: {
    cities: Object,
    hotCities: Array,
    letter: String
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  methods: {
    handleCityClick (city) {
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  computed: {
    ...mapState({
      'currentCity': 'city'
    })
  }
}
</script>

<style lang="scss" scoped>
    .list{
        position: absolute;
        top:1.58rem;
        left: 0;
        right: 0;
        bottom: 0;
        overflow: hidden;
        .title{
            line-height: .54rem;
            background: #eee;
            padding-left: .2rem;
            color:#666;
            font-size: .26rem;
        }
        .border-topbottom{
            &:before{
                border-color:#ccc;
            }
            &:after{
                border-color:#ccc;
            }
        }
        .border-bottom{
            &:before{
                border-color:#ccc;
            }
        }
        .button-list{
            padding: .1rem .6rem .1rem .1rem;
            overflow: hidden;
            .button-wrap{
                float: left;
                width: 33.33%;
                .button{
                    text-align: center;
                    margin: .1rem;
                    border: .02rem solid #ccc;
                    padding: .1rem 0;
                    border-radius: .06rem;
                }
            }
        }
        .item-list{
            .item{
                line-height: .76rem;
                padding-left: .2rem;
            }
        }
    }
</style>
