<template>
  <div class="tabs">
    <tabs card>
      <tab title="商品管理">商品管理2.0</tab>
      <tab title="图片空间">图片空间2.0</tab>
    </tabs>
    <br>
    <tabs :tabs="tabs"></tabs>
  </div>
</template>

<script>
import goods from './components/goods'
import sizes from './components/sizes'
import tab from './components/tab'
import tabs from './components/tabs'
import Vue from 'vue'

Vue.component( 'goods', goods )
Vue.component( 'sizes', sizes )

export default {
  data () {
    return {
      tabs: [{
        title: 111,
        component: 'goods'
      }, {
        title: 222,
        disabled: true,
        component: 'sizes'
      }, {
        title: 333,
        component: 'sizes'
      }]
    }
  },

  components: {
    tab,
    tabs
  }
}
</script>

<style>
html {
  width: 1000px;
  margin: 0 auto;
  height: 100%;
  padding: 20px;
}
a {
  color: #42b983;
  text-decoration: none;
}
.tabs {
  width: 400px;
}
</style>
