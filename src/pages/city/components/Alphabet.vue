<template>
  <ul class="list">
    <li class="item"
     v-for="item of letters"
     :key="item"
     :ref="item"
     @click="handleLetterClick"
     @touchstart="handleTouchStart"
     @touchmove="handleTouchMove"
     @touchend="handleTouchEnd"
     >
      {{item}}
     </li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  },
  updated () {
    // 定义startY等于列表区域距离顶部的距离
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
      console.log(this.letters)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          // // 定义touchY ,触摸屏幕到手指滑动的位置
          const touchY = e.touches[0].clientY - 79
          // touchY减去startY除以字母高度获取字母值
          const index = Math.floor((touchY - this.startY) / 20) // 20是一个字母的高度
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>

<style scoped lang="stylus">
@import '~@/assets/styles/varibles.styl'
  .list
    display flex
    flex-direction column
    position absolute
    width 0.4rem
    right .1rem
    top 1.58rem
    bottom 0
    justify-content center
    text-align center
    .item
      line-height .4rem
      text-align center
      color $bgColor
</style>
