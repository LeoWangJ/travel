<template>
    <div>
        <div class="banner" @click="handleBannerClick">
            <img class="banner-img" :src="bannerImg"/>
            <div class="banner-info">
                <div class="banner-info--title">{{sightName}}</div>
                <div class="banner-info--number"><span class="iconfont banner-icon">&#xe626;</span>{{this.gallaryImgs.length}}</div>
            </div>
        </div>
        <fade-animation>
          <gallery :imgs="gallaryImgs" v-show="showGallery" @close="handleGalleryClose"></gallery>
        </fade-animation>
    </div>
</template>

<script>
import Gallery from 'common/gallery/Gallery'
import FadeAnimation from 'common/fade/FadeAnimation'

export default {
  name: 'detailBanner',
  components: {
    Gallery,
    FadeAnimation
  },
  props: {
    sightName: String,
    bannerImg: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showGallery: false
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallery = true
    },
    handleGalleryClose () {
      this.showGallery = false
    }
  }
}
</script>

<style lang="scss" scoped>
    .banner{
        overflow: hidden;
        height: 0;
        padding-bottom: 55%;
        position: relative;
        &-img{
            widows: 100%;
        }
        &-info{
            display: flex;
            position: absolute;
            left: 0;
            bottom: 0;
            right: 0;
            line-height: .6rem;
            color:#fff;
            background-image: linear-gradient(to bottom,rgba(0,0,0,0),rgba(0,0,0,0.8));
            &--title{
                flex:1;
                font-size: .32rem;
                padding: 0 .2rem;
            }
            &--number{
                margin-top: .14rem;
                padding: 0 .4rem;
                line-height: .32rem;
                height: .32rem;
                border-radius: .2rem;
                background: rgba(0,0,0,.8);
                font-size: .24rem;
                .banner-icon{
                    font-size: .24rem;
                }
            }
        }
    }
</style>
