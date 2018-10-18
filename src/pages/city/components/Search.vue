<template>
  <div>
    <div class="search">
      <input class="input-search"  type="text" name="search"
      v-model="keyword"
      placeholder="输入城市名或拼音">
    </div>
    <div class="search-content"
    v-show="keyword"
    ref="searchCon"
    >
      <ul>
        <li class="search-list" v-for="item of list" :key="item.id"
        @click="handleCityChoose(item.name)">
        {{item.name}}</li>
        <li class="search-list" v-show="hasNoData">未找到相关城市</li>
      </ul>
    </div>
  </div>
</template>
<script>
import Bscroll from 'better-scroll'
import { mapMutations } from 'vuex'
export default{
  name: 'CitySearch',
  props: {
    obj: Object
  },
  data () {
    return {
      keyword: '',
      timer: null,
      list: []
    }
  },
  computed: {
    hasNoData () {
      return !this.list.length
    }
  },
  methods: {
    handleCityChoose (city) {
      // this.$store.commit('changeState', city)
      // 简单方法
      this.changeState(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeState'])
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let key in this.obj) {
          this.obj[key].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 ||
            value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.searchCon, {
      click: true
    })
  }
}
</script>
<style lang="stylus" scoped>
  .search
    height: 0.72rem
    padding: 0 0.1rem
    background: #00bcd4
    .input-search
      width: 100%
      box-sizing: border-box
      width: 100%
      height: .62rem
      padding: 0 .1rem
      line-height: .62rem
      text-align: center
      border-radius: .06rem
      color: #666
  .search-content
    z-index: 1
    overflow: hidden
    position: absolute
    top: 1.58rem
    left: 0
    right: 0
    bottom: 0
    background: #eee
    .search-list
      line-height: .62rem
      padding-left: .2rem
      background: #fff
      color: #666
</style>
