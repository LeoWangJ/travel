<template>
    <header class="header">
        <div class="header-left">
          <div class="iconfont back-icon">&#xe624;</div>
        </div>
        <div class="header-input">
          <span class="iconfont">&#xe632;</span>
          輸入城市/景點/遊玩主題
        </div>
        <router-link to="/city">
          <div class="header-right">
            {{this.city}}
            <span class="iconfont arrow-icon">&#xe64a;</span>
          </div>
        </router-link>
    </header>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="scss" scoped>
  @import '~styles/varibles.scss';

  .header{
    display:flex;
    line-height: $headerHeight;
    background-color: $bgColor;
    color: #fff;
    &-left{
      width: .64rem;
      float: left;
      .back-icon{
        text-align: center;
        font-size: .4rem;
      }
    }
    &-input{
      flex:1;
      background-color: #fff;
      border-radius: .1rem;
      margin-top: .12rem;
      height: .64rem;
      margin-left:.2rem;
      color: #ccc;
      line-height: .64rem;
      height: .64rem;
      padding-left: .2rem;
    }
    &-right{
      min-width: 1.04rem;
      padding: 0 .1rem;
      float: right;
      text-align: center;
      color:#fff;
      .arrow-icon{
        font-size: .24rem;
        margin-left: -.04rem;
      }
    }
  }
</style>
