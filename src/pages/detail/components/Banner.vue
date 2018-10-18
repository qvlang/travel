<template>
  <div>
    <div class="wrap" @click="handleShowClick">
      <div>
        <img :src="bannerImg"
        width="100%" :alt="sightName">
      </div>
      <div class="text-box">
        <div class="little-box">
          <span class="iconfont">&#xe691;</span>
          <em class="lt-txt">12</em>
        </div>
        <p class="desc-box">{{sightName}}</p>
      </div>
    </div>
    <common-gallary :imgs="bannerImgs" v-show="showGallary"
    @change="handleHiddenClick"
    ></common-gallary>
  </div>
</template>

<script>
import CommonGallary from '@/common/gallary/Gallary'
export default{
  name: 'DetailBanner',
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  components: {
    CommonGallary
  },
  data () {
    return {
      showGallary: false,
      imgs: ['http://img1.qunarzz.com/sight/p0/1502/3b/3ba9728f2448c5c3.water.jpg_r_800x800_868b0ab7.jpg',
        'http://img1.qunarzz.com/sight/p0/1502/47/47ce0707a80c6bd6.water.jpg_r_800x800_1b172fd2.jpg']
    }
  },
  methods: {
    handleShowClick () {
      this.showGallary = true
    },
    handleHiddenClick () {
      this.showGallary = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .wrap
    overflow: hidden
    height: 0
    padding-bottom: 55%
    position: relative
    .text-box
      position: absolute
      bottom: 0.2rem
      .little-box
        width: 1.2rem
        height: .4rem
        margin: 0.15rem 0.2rem
        background: rgba(0,0,0,.5)
        border-radius: .2rem
        font-size: .24rem
        color: #fff
        line-height: .4rem
        text-align: center
        .lt-txt
          margin-left: 0.1rem
      .desc-box
        margin-left: 0.2rem
        line-height: .4rem
        color: #fff
        font-size: .36rem
        text-shadow: 0 1px 2px rgba(0,0,0,0.70)
</style>
