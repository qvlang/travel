<template>
    <div class="header">
      <div class="header-left">
        <div class="iconfont back-icon">&#xe624;</div>
      </div>
      <div class="header-input">
        <span class="iconfont arrow-icon">&#xe632;</span>
        输入城市/景点/游玩主题
      </div>
      <router-link to="/City">
        <div class="header-right">{{this.city}}
          <span class="iconfont">&#xe6aa;</span>
        </div>
      </router-link>
    </div>
</template>
<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>
<style lang="stylus" scoped>
  @import '~@/assets/styles/iconfont/varibles.styl'
  .header
    height: .86rem
    display: flex
    color:#fff
    background: $bgcolor
    .header-left
      float: left
      width: .64rem
      line-height: .86rem
      .back-icon
        text-align: center
        font-size: .4rem
    .header-input
      height: .64rem
      flex: 1
      line-height: .64rem
      margin-top: .12rem
      margin-left: .2rem
      padding-left: .2rem
      background: #fff
      color: #ccc
      border-radius:.1rem
    .header-right
      min-width: 1.04rem
      padding: 0 0.1rem
      float: right
      text-align: center
      line-height: .86rem
      color: #fff
      .arrow-icon
        font-size: .24rem
        margin-left: -.04rem
</style>
