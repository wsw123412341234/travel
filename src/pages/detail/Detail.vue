<template>
  <div class="container">
    <DetailHeader></DetailHeader>
    <detail-banner
      :bannerImg="bannerImg"
      :sightName="sightName"
      :bannerImgs="gallaryImgs"
    >
    </detail-banner>
    <DetailList :list="list"></DetailList>
  </div>
</template>

<script>
import axios from 'axios'
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data () {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      list: []
    }
  },
  methods: {
    getDetailInfo () {
      axios.get('./static/mock/detail.json')
        .then(this.handleGetDataSucc)
    },
    handleGetDataSucc (res) {
      console.log(res)
      res = res.data
      if (res.ret && res.data) {
        const data = res.data
        this.bannerImg = data.bannerImg
        this.sightName = data.sightName
        this.gallaryImgs = data.gallaryImgs
        this.list = data.categoryList
      }
    }
  },
  mounted () {
    this.getDetailInfo()
  }
}
</script>

<style scoped lang="stylus">
  .container
    height 50rem
</style>
