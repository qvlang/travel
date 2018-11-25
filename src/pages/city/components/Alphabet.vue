<template>
  <div>
    <ul class="list clearfix">
      <li class="item"
        v-for="item of letters"
        :key="item"
        :ref="item"
        @click="handleLetterClick"
        @touchstart="handletouchstart"
        @touchmove="handletouchmove"
        @touchend="handletouchend"
      >
      {{item}}
      </li>
    </ul>
  </div>
</template>
<script>
export default{
  name: 'CityAlphabet',
  props: {
    obj: Object
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.obj) {
        letters.push(i)
      }
      return letters
    }
  },
  data () {
    return {
      startFlag: false,
      distanceA: 0,
      timer: null
    }
  },
  updated () {
    this.distanceA = this.$refs['A'][0].offsetTop
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handletouchstart () {
      this.startFlag = true
    },
    handletouchmove (e) {
      //函数节流避免事件过快执行
      if (this.startFlag) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const moveDistance = e.touches[0].clientY - 79
          const index = Math.floor((moveDistance - this.distanceA) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handletouchend () {
      this.startFlag = false
    }
  }
}
</script>
<style lang="stylus" scoped>
  .list
    display: flex
    flex-direction: column
    justify-content: center
    position: absolute
    top: 2.2rem
    right: 0.1rem
    .item
      line-height: .4rem
      text-align: center
      color: #00bcd4
</style>
