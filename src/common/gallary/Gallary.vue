<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options="swiperOptions">
        <swiper-slide v-for="(item, index) of bannerImgs" :key="index">
          <img class="gallary-img" :src="item" alt="">
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Gallary',
  props: {
    bannerImgs: Array,
    default () {
      return []
    }
  },
  data () {
    return {
      swiperOptions: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true,
        loop: true
      }
    }
  },
  methods: {
    handleGallaryClick () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow inherit
  .container
    display: flex
    flex-direction: column
    justify-content: center
    position fixed
    top 0
    left 0
    right 0
    bottom 0
    z-index 99
    background: #000
    .wrapper
      width 100%
      height 0
      padding-bottom 100%
      img
        width 100%
      .swiper-pagination
        bottom -1rem
        color #fff
</style>
