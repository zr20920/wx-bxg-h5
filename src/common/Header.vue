<template>
  <div class="header position-sticky bg-white flex flex-center flex-justify-between pv">
    <div class="left txt-info" @click="goBack()">{{ leftName }}</div>
    <p class="txt-center flex-1 txt-bold">{{title}}</p>
    <div class="right">
      <slot/>
    </div>
  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
  name: 'Header',
  props: {
    leftName: {
      type: String,
      default: '',
    },
    title: {
      type: String,
      default: '',
    },
  },
  computed: {
    ...mapState(['headerTips', 'input']),
  },
  mounted() {
    this.FAKE_ACTION('june')
  },
  methods: {
    ...mapActions(['FAKE_ACTION']),
    goBack() {
      window.history.back()
    }
  },
}
</script>

<style lang="less">
.header {
  height: 40px;
  .left, .right {
    width: 80px;
  }
}
</style>
