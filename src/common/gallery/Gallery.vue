<template>
    <div class="container" @click="handleGalleryClick">
        <div class="wrapper">
            <swiper :options="swiperOption" >
                <swiper-slide v-for="(item, index) in imgs" :key="index">
                    <img class="gallery-img" :src="item"/>
                </swiper-slide>
                <div class="swiper-pagination"  slot="pagination"></div>
            </swiper>
        </div>
    </div>
</template>

<script>
export default {
  name: 'gallery',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        loop: true,
        observeParents: true,
        observer: true
      },
      list: [1]
    }
  },
  methods: {
    handleGalleryClick () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="scss" scoped>
    .container{
        display: flex;
        flex-direction: column;
        justify-content: center;
        position: fixed;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        background: #010101;
        z-index: 99;
        .wrapper{
            width: 100%;
            height: 0;
            padding-bottom: 100%;
            .gallery-img{
              width: 100%;
            }
            .swiper-pagination{
               color:#fff;
               bottom: -1rem;
            }
        }
        /deep/ .swiper-container{
            overflow: inherit;
        }
    }
</style>
