<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市/景点/游玩主题
    </div>
    <router-link to="././City">
      <div class="header-right">
        {{this.city}}
        <span class="iconfont arrow-icon">&#xe64a;</span>
      </div>
    </router-link>
  </div>
</template>
<script>
import {mapState} from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
  // props: {
  //   lastCity: String
  // }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus">
@import '~styles/varibles.styl'
.header
  display: flex
  color: $darkTextColor
  background-color :$bgColor
  line-height:$headerHeight
  .header-left
    width:0.64rem
    float:left
    .back-icon
      text-align: center
      font-size: .4rem
  .header-input
    flex:1
    height: .64rem
    line-height: .64rem
    margin-top: .12rem
    margin-left: .2rem
    padding-left: .2rem
    background: #fff
    border-radius: .1rem
    box-sizing:border-box
    color: #ccc
  .header-right
    min-width:1.04rem;
    float: right
    text-align: center
    color: #fff
    padding: 0 .1rem
</style>
