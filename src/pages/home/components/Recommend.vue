<template>
  <div>
    <div class="title">
      <img class="title-img" src="http://img1.qunarzz.com/piao/fusion/1711/89/ebc329f16c55bb02.png">
      <p class="title-desc">猜你喜欢</p>
    </div>
    <ul>
      <router-link tag="li" class="item border-bottom"
        v-for="item of list"
        :to="'/Detail/' + item.id"
        :key=item.id>
          <img class="item-img" :src="item.imgUrl" alt="图片">
          <div class="item-info">
            <p class="info-title">{{item.title}}</p>
            <p class="info-desc">{{item.desc}}</p>
            <button class="info-bt">查看详情</button>
          </div>
      </router-link>
    </ul>
  </div>
</template>
<script>
export default{
  name: 'HomeRecommend',
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
    .title-img
      margin-left: 0.15rem
      height: 100%
    .title-desc
      display: inline-block
      margin-left: 0.1rem
      font-size: 0.36rem
  .item
    height: 2.4rem
    padding: 0.26rem 0
    display: flex
    .item-img
      height: 100%
    .item-info
      flex: 1
      height: 100%
      margin-left: 0.2rem
      .info-title
        height: 0.44rem
        margin-top: 0.26rem
        font-size: 0.32rem
        line-height: 0.44
        color: #000
      .info-desc
        margin-top: 0.14rem
        height: 0.34
        line-height: 0.34rem
      .info-bt
        margin-top: .22rem
        color: #616161
        font-size: .24rem
        line-height: .4rem
        border-radius: 0.15rem
        background: #ff8300
</style>
