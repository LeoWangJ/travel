<template>
  <div>
    <div class="title">週末去哪兒</div>
    <ul>
      <li class="item border-bottom" v-for="item of list" :key="item.id">
        <div class="item-img-wrap">
          <img class="item-img" :src="item.imgUrl" alt="">
        </div>
        <div class="item-info">
          <p class="item-info-title">{{item.title}}</p>
          <p class="item-info-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'weekend',
  props: {
    list: Array
  }
}
</script>

<style lang="scss" scoped>
@import '~styles/mixins.scss';

.title{
  line-height: .8rem;
  background: #eee;
  text-indent: .2rem;
}
.item{
  &-img-wrap{
    height: 0;
    overflow: hidden;
    padding-bottom: 37.09%;
  }
  &-img{
    width: 100%;
  }
  &-info{
      padding: .1rem;
    &-title{
      @include ellipsis();
      line-height: .54rem;
      font-size: .32rem;
    }
    &-desc{
      @include ellipsis();
      line-height: .4rem;
      color: #ccc;
    }
  }
}
</style>
