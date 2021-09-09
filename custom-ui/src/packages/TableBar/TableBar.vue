<template>
  <div class="page">
    <div class="table-bar_wrapper" :style="`height:${tableHeight}`">
      <slot></slot>
    </div>
    <div class="fill" :style="`height:${tableHeight}`"></div>
  </div>
</template>

<script>
export default {
  name: 'TableBar',
  props: {
    height: {
      type: [String, Number],
      default: '200'
    }
  },
  data() {
    return {}
  },

  methods: {},
  computed: {
    tableHeight() {
      console.log(this.height.indexOf('%'), '为什么没有')
      if (this.height.indexOf('%') != -1) return this.height
      if (this.height.indexOf('px') != -1) return this.height
      if (this.height.indexOf('vh') != -1) return this.height
      if (String(Number(this.height)) != 'NaN') return `${this.height}px`
    }
  }
}
</script>

<style lang="scss" scoped>
.page {
  width: 100%;
  height: 100%;
  position: relative;
  .table-bar_wrapper {
    width: 100vw;
    // background: yellowgreen;
    position: fixed;
    left: 0;
    bottom: 0;
    z-index: 999 !important;
  }
  .fill {
    position: relative;
    left: 0;
    bottom: 0;
    // background: pink;
    width: 100vw;
  }
}
</style>


