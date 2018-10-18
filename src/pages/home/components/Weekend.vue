<template>
  <div>
    <div class="title">
      <p class="title-desc">周末去哪</p>
    </div>
    <ul>
      <li class="item border-bottom" v-for="item of list"
      :key=item.id>
        <div class="item-img-wrap">
          <img class="item-img" :src="item.imgUrl" alt="当地人游深圳">
        </div>
        <div class="item-info">
          <p class="info-title">{{item.title}}</p>
          <p class="info-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default{
  name: 'HomeWeekend',
  props: {
    list: Array
  }
}
</script>
<style lang="stylus" scoped>
  .title
    height: 0.94rem
    padding: 0.24rem 0 0.26rem
    box-sizing: border-box
    .title-desc
      margin-left: 0.2rem
      font-size: 0.36rem
  .item-img-wrap
    overflow: hidden
    height: 0
    padding-bottom: 37.4375%
    .item-img
      width: 100%
  .item-info
    height: 1rem
    padding: .14rem .2rem .2rem .2rem
    .info-title
      height: 0.34rem
      margin-top: 0.16rem
      font-size: 0.22rem
      line-height: 0.34rem
      color: #000
    .info-desc
      margin-top: 0.14rem
      height: 0.34rem
      line-height: 0.34rem
</style>
