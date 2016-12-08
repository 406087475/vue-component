<template>
  <div class="tabs-wrap">
    <ul class="tabs-header" :class="{ 'card': card }">
      <template v-for="tab in tabs">
        <li v-if="!tab.disabled" :class="{ 'active': active === $index }" @click="switchTab( $index, tab )" data-title="{{ tab.title }}"></li>
        <li v-else class="disabled" data-title="{{ tab.title }}"></li>
      </template>
    </ul>

    <div class="tabs-content">
      <slot>
        <template v-for="tab in tabs">
          <component v-if="$index === active && !tab.disabled" :is="tab.component"></component>
        </template>
      </slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tabs: {
      type: Array,
      default () {
        return []
      }
    },
    active: {
      type: Number,
      default: 0
    },
    card: Boolean
  },

  data () {
    return {

    }
  },

  methods: {
    switchTab ( index, tab ) {
      this.active = Number( index )
    }
  }
}
</script>

<style scoped>
ul,
ul li {
  margin: 0;
  padding: 0;
  list-style: none;
}
.tabs-header {
  border-bottom: #ddd 1px solid;
}
.tabs-header li {
  display: inline-block;
  padding: 5px 0;
  cursor: pointer;
}
.tabs-header li:after {
  padding: 6px 20px;
  content: attr(data-title);
  border: #fff 1px solid;
  border-bottom: #ddd 1px solid;
}
.tabs-header .active:after {
  color: #108ee9;
  border-bottom: #108ee9 1px solid;
}
.tabs-header .disabled:after {
  color: #999;
  cursor: not-allowed;
}

.card .active:after {
  border: #ddd 1px solid;
  border-bottom: #fff 1px solid;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}
.card li:hover {
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  background: #eee;
}
.card .active:hover,
.card .disabled:hover {
  background: #fff;
  cursor: inherit;
}

.tabs-content {
  padding: 10px 5px;
}
</style>
