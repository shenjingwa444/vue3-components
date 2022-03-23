<template>
  <div>
    <div v-for="(t,index) in titles" :key='index'>{{t}}</div>
    <component v-for="(c,index) in defaults" :key="index" :is="c"/>
  </div>
</template>

<script lang="ts">
import Tab from './Tab.vue'
export default {
  setup(props,context){
    const defaults = context.slots.default()
    const titles = defaults.map(tag=>tag.props.title)
    defaults.forEach((tag)=>{
      if(tag.type !== Tab){
        throw new Error('Tabs 字标签必须是 Tab')
      }
    })
    return {defaults,titles}
  }
}
</script>