<template>
  <div class="container">
    <swiper indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
      <swiper-item v-for="item in imgUrls" :key="item">
        <image :src="item" class="slide-image" width="355" height="150"/>
      </swiper-item>
    </swiper>
    <div class="label"></div>
    <div class="list">
      <mptoast/>
    </div>
  </div>
</template>

<script>
import card from '@/components/card'
import mptoast from 'mptoast'
// import { post } from 'src/utils/requestMethods.js'

export default {
  data () {
    return {
      userInfo: {},
      indicatorDots: false,
      autoplay: false,
      interval: 3000,
      duration: 3000,
      imgUrls: [
        'http://dummyimage.com/200x100/00405d/f00&text=Mock.js',
        'http://dummyimage.com/200x100/00405d/F0F&text=Mock.js',
        'http://dummyimage.com/200x100/00405d/FF0&text=Mock.js'
      ]
    }
  },

  components: {
    card, mptoast
  },

  mounted () {
    this.showToast()
  },

  methods: {
    getList () {
      // let res = await post ('goods/list', {name: 'liuting'})
    },
    showToast () {
      this.$mptoast('我是提示信息')
    },
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    }
  },
  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  }
}
</script>

<style scoped>

</style>
