<template>
  <div>
    <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
      <div class="iconfont header-abs-back">&#xe624;</div>
    </router-link>
    <div class="header-fixed" v-show="!showAbs"
    :style="opacityStyle"
    >景点选择
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe624;</div>
    </router-link>
    </div>
  </div>
</template>

<script>
export default{
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop || document.body.scrollTop
      if (top > 40) {
        let opacity = top / 100
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = { opacity }
        this.showAbs = false
      }
      else {
        this.showAbs = true
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  .header-abs
    position: absolute
    top: 0.2rem
    left: 0.2rem
    width: 0.6rem
    height: 0.6rem
    text-align: center
    line-height: 0.6rem
    border-radius: 0.3rem
    background: rgba(0, 0, 0, 0.8)
    .header-abs-back
      color: #fff
      font-size: 0.3rem
  .header-fixed
    position: fixed
    top: 0
    left: 0
    right: 0
    height: 0.86rem
    line-height: 0.86rem
    text-align: center
    background: #00bcd4
    color: #fff
    font-size: 0.32rem
    .header-fixed-back
      width: 0.64rem
      float: left
      text-align: center
      font-size: .4rem
      color: #fff
</style>
