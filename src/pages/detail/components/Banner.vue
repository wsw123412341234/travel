<template>
  <div class="wrapper">
    <div class="banner" @click="handleBannerClick" >
      <img :src="bannerImg" alt="">
      <div class="banner-info">
        <div class="banner-tittle">
          {{this.sightName}}
        </div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe692;</span>
          {{this.bannerImgs.length}}
        </div>
      </div>
    </div>
    <fade-Animation>
      <gallary
        :bannerImgs="bannerImgs"
        :showGallary="showGallary"
        @close="closeGallary"
        v-show="showGallary"
      >
      </gallary>
    </fade-Animation>
  </div>
</template>

<script>
import Gallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  props: {
    bannerImg: String,
    bannerImgs: Array,
    sightName: String
  },
  components: {
    Gallary,
    FadeAnimation
  },
  data () {
    return {
      showGallary: false
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    closeGallary () {
      this.showGallary = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .wrapper
     z-index 10
    .banner
      position: relative
      overflow: hidden
      height: 0
      padding-bottom: 55%
      .banner-img
        width: 100%
      .banner-info
        display: flex
        position: absolute
        left: 0
        right: 0
        bottom: 0
        line-height: .6rem
        color: #fff
        background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
        .banner-tittle
          flex: 1
          font-size: .32rem
          padding: 0 .2rem
        .banner-number
          height: .32rem
          line-height: .32rem
          margin-top: .14rem
          padding: 0 .4rem
          border-radius: .2rem
          background: rgba(0, 0, 0, .8)
          font-size: .24rem
          .banner-icon
            font-size: .24rem
</style>
