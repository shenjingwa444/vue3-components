<template>
  <div class="pixu-tabs">
    <div class="pixu-tabs-nav">
      <div class="pixu-tabs-nav-item" v-for="(t,index) in titles" :key='index'>{{ t }}</div>
    </div>
    <div class="pixu-tabs-content">
      <component class="pixu-tabs-content-item" v-for="(c,index) in defaults" :key="index" :is="c"/>
    </div>
  </div>
</template>

<script lang="ts">
import Tab from './Tab.vue';

export default {
  setup(props, context) {
    const defaults = context.slots.default();
    const titles = defaults.map(tag => tag.props.title);
    defaults.forEach((tag) => {
      if (tag.type !== Tab) {
        throw new Error('Tabs 字标签必须是 Tab');
      }
    });
    return {defaults, titles};
  }
};
</script>

<style lang="scss">
$blue:#40a9ff;
$color:#333;
$border-color:#d9d9d9;

.pixu-tabs{
  &-nav{
    display: flex;
    color:$color;
    border-bottom:1px solid $border-color;
    &-item{
      padding:8px 0;
      margin:0 16px;
      cursor:pointer;
      &:first-child{
        margin-left:0;
      }
      &.selected{
        color:$blue;
      }
    }
  }
  &-content{
    padding:8px 0;
  }
}
</style>