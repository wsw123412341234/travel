<template>
  <div>
    <div class="title">热销推荐</div>
    <ul>
      <router-link
        tag="li"
        class="item border-bottom"
        :to="'/detail/' + item.id"
        v-for="item of list"
        :key="item.id"
      >
        <img :src="item.imgUrl" />
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    list: {
      list: Array
    }
  },
  data () {
    return {
      // 'recommendList': [
      //   {
      //     'id': '001',
      //     'imgUrl': 'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_140x140_80f63803.jpg',
      //     'title': '故宫',
      //     'desc': '东方宫殿建筑代表，世界宫殿建筑典范'
      //   },
      //   {
      //     'id': '002',
      //     'imgUrl': 'http://img1.qunarzz.com/sight/p0/1511/d2/d2aec2dfc5aa771290.water.jpg_140x140_abb362a7.jpg',
      //     'title': '故宫',
      //     'desc': '东方宫殿建筑代表，世界宫殿建筑典范'
      //   },
      //   {
      //     'id': '003',
      //     'imgUrl': 'http://img1.qunarzz.com/sight/p0/1501/f4/f467729126949c3a.water.jpg_140x140_ef235b1c.jpg',
      //     'title': '故宫',
      //     'desc': '东方宫殿建筑代表，世界宫殿建筑典范'
      //   }
      // ]
    }
  }
}
</script>

<style scoped lang="stylus">
@import '~@/assets/styles/mixins.styl'
  .title
    margin-top: .2rem
    line-height: .8rem
    background: #eee
    text-indent: .2rem
  .item
    overflow: hidden
    display: flex
    height: 1.9rem
    .item-img
      width: 1.7rem
      height: 1.7rem
      padding: .1rem
    .item-info
      flex: 1
      padding: .1rem
      min-width: 0
      .item-title
        line-height: .54rem
        font-size: .32rem
        ellipsis()
      .item-desc
        line-height: .4rem
        color: #ccc
        ellipsis()
      .item-button
        line-height: .44rem
        margin-top: .16rem
        background: #ff9300
        padding: 0 .2rem
        border-radius: .06rem
        color: #fff
</style>
