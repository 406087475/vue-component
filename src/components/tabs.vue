<template>
  <div class="tabs">
    <ul class="tabs-header">
      <li
        v-for="tab in tabs"
        :class="{ 'active': active === $index, 'disabled': tab.disabled }"
        @click="switchTab( $index, tab )"
        data-title="{{ tab.title }}">
      </li>
    </ul>

    <div class="tabs-content">
      <slot>
        <template v-for="tab in tabs">
          <component v-if="$index === active" :is="tab.component"></component>
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
    }
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
}
.tabs-header li:after {
  padding: 6px 20px;
  cursor: pointer;
  content: attr(data-title);
  border-bottom: #ddd 1px solid;
}
.tabs-header .active:after {
  color: #108ee9;
  font-weight: bold;
  border-bottom: #108ee9 1px solid;
}
.tabs-header .disabled:after {
  color: #999;
  cursor: not-allowed;
}
.tabs-content {
  padding: 10px 5px;
}
</style>
