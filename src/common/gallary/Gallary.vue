<template>
  <div class="container" @click="handleHidden">
    <div class="wrapper" :options="swiperOptions">
      <swiper>
        <!-- slides -->
        <swiper-slide v-for="(item, index) in imgs" :key="index">
          <img class="gallary-img" :src="item"  alt="旅游图片">
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOptions: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observe: true
      }
    }
  },
  methods: {
    handleHidden () {
      this.$emit('change')
    }
  }
}
</script>
<style lang="stylus" scoped>
  .container
    display: flex
    flex-direction: column
    justify-content: center
    z-index: 99
    overflow: hidden
    position: fixed
    top: 0
    right: 0
    left: 0
    bottom: 0
    background: #000
    .wrapper
      overflow: hidden
      width: 100%
      height: 0
      padding-bottom: 66.75%
      background: #fff
      .gallary-img
        width: 100%
      .swiper-pagination
        color: #fff
</style>
