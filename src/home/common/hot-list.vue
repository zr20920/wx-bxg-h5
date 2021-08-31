<template>
  <div class="hot-list pv mt-10">
    <div class="title h-40 flex flex-align-center flex-justify-between">
      <div class="txt-bold">热门产品</div>
      <div class="txt-link">更多></div>
    </div>
    <div class="grid">
      <div class="grid-item p-10 border-8" v-for="(item, index) in list" :key="index" @click="onItem(item)">
        <img class="img" :src="item.img" alt="">
        <div class="txt-14">{{ item.name }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import { GRID_LIST } from '../config'

export default Vue.extend({
  name: 'hot-list',
  // props: {
  //   list: {
  //     type: Array,
  //     default: [],
  //   },
  // },
  data() {
    return {
      list: GRID_LIST,
    }
  },
  created() {},
  methods: {
    onItem(item) {
      console.log('onItem', item)
    },
  },
})
</script>

<style lang="less">
.hot-list {
  .grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr); /* 相当于 1fr 1fr 1fr */
    // grid-template-rows: repeat(2, 1fr); /* fr单位可以将容器分为几等份 */
    grid-gap: 1%; /* grid-column-gap 和 grid-row-gap的简写 */
    grid-auto-flow: row;
    .grid-item {
      color: #fff;
      // text-align: center;
      background: linear-gradient(to bottom,
        #f5f6f6 0%,
        #dbdce2 21%,
        #b8bac6 49%,
        #dddfe3 80%,
        #f5f6f6 100%);
      .img {
        // width: 60px;
        width: 100%;
        height: 60px;
      }
    }
  }
}
</style>
