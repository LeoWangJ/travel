<template>
    <div class="header">
        <router-link to="/" tag="div" class="header-abs" v-show="showAbs">
            <span class="iconfont back-icon header-abs-black">&#xe624;</span>
        </router-link>
        <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
            <router-link to="/">
                <div class="iconfont header-fixed-back">&#xe624;</div>
            </router-link>
            景點詳情
        </div>
    </div>
</template>

<script>
export default {
  name: 'detailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll () {
      let top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {
          opacity
        }
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '~styles/varibles.scss';
  .header{
    &-abs{
        position: absolute;
        left: .2rem;
        top: .2rem;
        width: .8rem;
        height: .8rem;
        line-height: .8rem;
        text-align: center;
        border-radius: .4rem;
        background: rgba(0,0,0,.8);
        &-black{
            color: #fff;
            font-size: .4rem;
        }
    }
    &-fixed{
        z-index: 2;
        position: fixed;
        overflow: hidden;
        top: 0;
        left: 0;
        right: 0;
        height: $headerHeight;
        line-height: $headerHeight;
        color:#fff;
        text-align: center;
        background: $bgColor;
        font-size: .32rem;
        &-back{
            width: .64rem;
            text-align: center;
            font-size: .4rem;
            position: absolute;
            top:0;
            left: 0;
            color:#fff;
        }
    }
  }
</style>
