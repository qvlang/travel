<template>
  <div class="city-header">城市选择
    <router-link to="/">
      <div class="iconfont back-city">&#xe624;</div>
    </router-link>
  </div>
</template>
<script>
export default{
  name: 'CityHeader'
}
</script>
<style lang="stylus" scoped>
  .city-header
    height: 0.86rem
    line-height: 0.86rem
    text-align: center
    background: #00bcd4
    color: #fff
    font-size: 0.32rem
    .back-city
      width: 0.64rem
      float: left
      text-align: center
      font-size: .4rem
      color: #fff
</style>
