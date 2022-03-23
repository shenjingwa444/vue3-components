<template>
  <div class="pixu-tabs">
    <div class="pixu-tabs-nav">
      <div :class="{selected:t===selected}" @click="select(t)" class="pixu-tabs-nav-item" v-for="(t,index) in titles" :key='index'>{{ t }}</div>
    </div>
    <div class="pixu-tabs-content">
      <component :is="current" :key="current.props.title" class="pixu-tabs-content-item"/>
      {{current.props.title}}
    </div>
  </div>
</template>

<script lang="ts">
import Tab from './Tab.vue';
import {computed} from 'vue';

export default {
  props:{
    selected:{
      type:String,
    }
  },
  setup(props, context) {
    const defaults = context.slots.default();
    const titles = defaults.map(tag => tag.props.title);
    const current = computed(()=>{
      return defaults.filter((tag)=>{
        return tag.props.title === props.selected
      })[0]
    })
    defaults.forEach((tag) => {
      if (tag.type !== Tab) {
        throw new Error('Tabs 字标签必须是 Tab');
      }
    });
    const select = (title)=>{
      context.emit('update:selected',title)
    }
    return {defaults, titles,current,select};
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