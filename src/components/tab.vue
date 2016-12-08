<template>
  <div class="tabs-tiem" v-show="isShow">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    index: {
      type: Number,
      default: null
    },
    disabled: Boolean,
    dataRender: Boolean
  },

  data () {
    return {
      isShow: false
    }
  },

  created () {
    let vm = this
    if ( vm.dataRender ) return

    let parent = vm.$parent
    let tabs = parent.tabs
    let index = tabs.length

    tabs.push({
      index,
      title: vm.title,
      disabled: vm.disabled
    })

    vm.index = index
  },

  computed: {
    isShow () {
      return this.$parent.active === this.index
    }
  }
}
</script>

<style scoped>

</style>
