<template>
  <div>
    <div class="title">熱銷推薦</div>
    <ul>
        <router-link :to="'/detail/'+item.id" tag="li" class="item border-bottom" v-for="item of list" :key="item.id">
          <img class="item-img" :src="item.imgUrl" alt="">
          <div class="item-info">
            <p class="item-info-title">{{item.title}}</p>
            <p class="item-info-desc">{{item.desc}}</p>
            <button class="item-info-button">查看詳情</button>
          </div>
        </router-link>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'recommand',
  props: {
    list: Array
  }
}
</script>

<style lang="scss" scoped>
@import '~styles/mixins.scss';

.title{
  margin-top: .2rem;
  line-height: .8rem;
  background: #eee;
  text-indent: .2rem;
}
.item{
  display: flex;
  height: 1.9rem;
  overflow: hidden;
  &-img{
    height: 1.7rem;
    width: 1.7rem;
    padding: .1rem;
  }
  &-info{
    flex:1;
    padding: .1rem;
    min-width: 0;
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
    &-button{
      background: #ff9300;
      padding: 0 .2rem;
      border-radius: .06rem;
      margin-top: .16rem;
      color:#fff;
      line-height: .44rem;
    }
  }
}
</style>
