<template>
    <div>
        <div class="item" v-for="(item, index) of list" :key="index">
            <div class="item-title border-bottom">
                <span class="item-title-icon"></span>
                {{item.title}}
            </div>
            <div v-if="item.children" class="item-children">
                <detail-list :list="item.children"></detail-list>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'detailList',
  props: {
    list: Array
  }
}
</script>

<style lang="scss" scoped>
 .item{
    &-title{
        line-height: .8rem;
        font-size: .32rem;
        padding:  0 .2rem;
        &-icon{
            display: inline-block;
            position: relative;
            width: .36rem;
            height: .36rem;
            top: .06rem;
            left: .06rem;
            background: url(//s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat;
            margin-right: .1rem;
            background-size: .4rem 3rem;
        }
    }
    &-children{
        padding: 0 .2rem;
    }
 }
</style>
