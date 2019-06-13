<template>
    <div class="header">
      <router-link to="/">
        <div class="iconfont header-back">&#xe624;</div>
      </router-link>
      城市選擇
    </div>
</template>

<script>
export default {
  name: 'cityHeader'
}
</script>

<style lang="scss" scoped>
  @import '~styles/varibles.scss';
  .header{
    overflow: hidden;
    height: $headerHeight;
    line-height: $headerHeight;
    color:#fff;
    text-align: center;
    background: $bgColor;
    font-size: .32rem;
    position: relative;
    .header-back{
      width: .64rem;
      text-align: center;
      font-size: .4rem;
      position: absolute;
      top:0;
      left: 0;
      color:#fff;
    }
  }
</style>
