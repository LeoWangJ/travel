<!-- The ref attr used to find the swiper instance -->
<template>
  <div class="swiper-wrap">
    <swiper :options="swiperOption" v-if="showSwiper">
      <swiper-slide v-for="item of list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl"/>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'carrousel',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}
</script>

<style lang="scss" scoped>
.swiper-wrap{
  width: 100%;
  overflow: hidden;
  height: 0;
  padding-bottom: 31.1%;
  background: #eee;
  /deep/ .swiper-pagination-bullet-active{
    background:#fff;
  }
  .swiper-img{
    width: 100%;
  }
}
</style>
