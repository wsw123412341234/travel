<template>
 <div class="wrapper" v-if="showSwiper">
    <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide
        v-for="item of list"
        :key="item.id"
        >
          <img class="swiper-img" :src="item.imgUrl" alt="">
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
      // swiperList: [
      //   {
      //     'id': '001',
      //     'imgUrl': 'http://img1.qunarzz.com/piao/fusion/1801/1a/94428c6dea109402.jpg_640x200_2cf590d8.jpg'
      //   },
      //   {
      //     'id': '002',
      //     'imgUrl': 'http://img1.qunarzz.com/piao/fusion/1802/42/7c92b9a381e46402.jpg_640x200_1cdce2a4.jpg'
      //   },
      //   {
      //     'id': '003',
      //     'imgUrl': 'http://img1.qunarzz.com/piao/fusion/1802/51/e78f936a5b404102.jpg_640x200_c14f0b3a.jpg'
      //   },
      //   {
      //     'id': '004',
      //     'imgUrl': 'http://img1.qunarzz.com/piao/fusion/1712/91/a275569091681d02.jpg_640x200_0519ccb9.jpg'
      //   }
      // ]
    }
  },
  computed: {
    showSwiper () {
      return this.list.length
    }
  }
}
</script>
<style lang="stylus" scoped>
  .wrapper >>> .swiper-pagination-bullet
    background-color:red !important
  .wrapper
    overflow: hidden
    width: 100%
    height: 0
    padding-bottom: 31.25%
    background: #eee
    .swiper-img
      width:100%;
</style>
