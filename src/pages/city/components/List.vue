<template>
  <div class="list clearfix" ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="city-btn">
          <router-link to="/">
            <div class="btn-wrap">
              <div class="btn">{{this.currentCity}}</div>
            </div>
          </router-link>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="city-btn">
          <div class="btn-wrap"
          v-for="item of list"
          :key="item.id"
          @click="handleCityChoose(item.name)"
          >
            <div class="btn">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item, key) of obj" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <ul v-for="liitem of item" :key="liitem.id">
          <li class="li-city" @click="handleCityChoose(liitem.name)">
          {{liitem.name}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default{
  name: 'CityList',
  props: {
    list: Array,
    obj: Object,
    letter: String
  },
  computed: {
    ...mapState({
      currentCity: 'city'
    })
  },
  methods: {
    handleCityChoose (city) {
      // this.$store.commit('changeState', city) 常规操作
      // 简单方法
      this.changeState(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeState'])
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper, {
      click: true
    })
  }
}
</script>
<style lang="stylus" scoped>
  .border-topbottom
    &:before
      border-color: #ccc
    &:after
      border-color: #ccc
  .border-bottom
    &:before
      border-color: #ccc
  .list
    position: absolute
    top: 1.58rem
    left: 0
    right: 0
    bottom: 0
    .title
      line-height: .54rem
      background: #eee
      padding-left: .2rem
      color: #666
      font-size: .26rem
    .city-btn
      overflow: hidden
      padding: .1rem .6rem .1rem .1rem
      .btn-wrap
        width:33.33%
        float: left
        .btn
          height: 0.5rem
          margin: 0.1rem
          text-align: center
          line-height: 0.5rem
          border: .02rem solid #ccc
          border-radius: .06rem
          color: #000
    .li-city
      line-height: .76rem
      padding-left: .2rem
</style>
