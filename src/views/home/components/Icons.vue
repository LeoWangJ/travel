<template>
    <div class="icons">
      <swiper :options="swiperOption" >
        <swiper-slide v-for="(page,index) of pages" :key="index">
          <div class="icon" v-for="item of page" :key="item.id">
            <div class="icon-img">
              <img class="icon-img-content" :src="item.imgUrl"/>
            </div>
            <p class="icon-desc">{{item.desc}}</p>
          </div>
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
</template>

<script>
export default {
  name: 'icons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)

        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '~styles/mixins.scss';
  .icons{
    margin-top: .1rem;
    /deep/ .swiper-container{
      height: 0;
      overflow: hidden;
      padding-bottom: 50%;
    }
    .icon{
      width: 25%;
      height: 0;
      padding-bottom: 25%;
      float: left;
      position: relative;
      &-img{
        position: absolute;
        top:0;
        left: 0;
        right: 0;
        bottom: .44rem;
        box-sizing: border-box;
        padding: .1rem;
        &-content{
          display: block;
          margin:0 auto;
          height: 100%;
        }
      }
      &-desc{
        position: absolute;
        left: 0;
        right:0;
        bottom: 0;
        line-height: .44rem;
        height: .44rem;
        color:#333;
        text-align: center;
        @include ellipsis
      }
    }
  }
</style>
