<template>
  <div class="home flex-ver">
    <Header title="首页" leftName=""></Header>
    <wx-swiper
      :indicator-dots="true"
      :circular="true"
      :autoplay="true"
      class="banner"
    >
      <wx-swiper-item v-for="(item, index) in background" :key="index" >
        <img class="img" :src="require('@/assets/img/img_bs1.png')" alt="">
      </wx-swiper-item>
    </wx-swiper>
    <!-- 九宫格 -->
    <Grid/>
    <!-- 热门产品 -->
    <hot-list/>
    <!-- 样式隐藏 -->
    <Footer></Footer>
  </div>
</template>

<script>
import Vue from 'vue'
import Header from '../common/Header.vue'
import Footer from '../common/Footer.vue'
import Grid from './common/grid.vue'
import HotList from './common/hot-list.vue'

export default Vue.extend({
  name: 'Home',
  components: {
    Header,
    Footer,
    Grid,
    HotList,
  },
  data() {
    return {
      background: [1, 2, 3]
    }
  },
  created() {
    window.addEventListener('wxload', query => console.log('page1 wxload', query))
    window.addEventListener('wxshow', () => console.log('page1 wxshow'))
    window.addEventListener('wxready', () => console.log('page1 wxready'))
    window.addEventListener('wxhide', () => console.log('page1 wxhide'))
    window.addEventListener('wxunload', () => console.log('page1 wxunload'))

    if (process.env.isMiniprogram) {
      console.log('I am in miniprogram')
    } else {
      console.log('I am in Web')
    }
  },
  methods: {
    onClickJump() {
      window.location.href = '/test/list/123'
    },

    onClickOpen() {
      window.open('/test/detail/123')
    },
  },
})
</script>

<style lang="less">
.home {
  height: 100%;
  .banner {
    width: 100%;
    height: 150px;
    .img {
      width: 100%;
      height: 150px;
    }
  }
}

a, button {
  display: block;
  width: 100%;
  height: 30px;
  line-height: 30px;
  text-align: center;
  font-size: 20px;
  border: 1px solid #ddd;
}

.miniprogram-root {
  .for-web {
    display: none;
  }
}
</style>
