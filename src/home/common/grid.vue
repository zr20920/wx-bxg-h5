<template>
  <div class="grid mt-10">
    <div class="grid-item p-20" v-for="(item, index) in list" :key="index" @click="onItem(item)">
      <img class="img border-8" :src="item.img" alt="">
      <div>{{ item.name }}</div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import { GRID_LIST } from '../config'

export default Vue.extend({
  name: 'Grid',
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
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 相当于 1fr 1fr 1fr */
  // grid-template-rows: repeat(2, 1fr); /* fr单位可以将容器分为几等份 */
  grid-gap: 1%; /* grid-column-gap 和 grid-row-gap的简写 */
  grid-auto-flow: row;
  .grid-item {
    color: #fff;
    text-align: center;
    background: linear-gradient(to bottom,
      #f5f6f6 0%,
      #dbdce2 21%,
      #b8bac6 49%,
      #dddfe3 80%,
      #f5f6f6 100%);
    .img {
      width: 60px;
      height: 60px;
    }
  }
}
</style>
