<template>
  <transition>
    <slot> </slot>
  </transition>
</template>

<script>
export default {
  name: 'Fade'
}
</script>

<style lang="scss" scoped>
  .v-enter, .v-leave-to{
      opacity: 0;
  }
  .v-enter-active, .v-leave-active{
    transition: opacity 0.5s;
  }
</style>
