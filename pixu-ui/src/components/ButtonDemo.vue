<template>
  <div>
    Button 示例
  </div>
  <h1>示例1</h1>
  <div>
    <Button>你好</Button>
    <Button @click="onClick">你好</Button>
    <Button theme="button">你好</Button>
    <Button theme="link">你好</Button>
    <Button theme="text">你好</Button>
  </div>
  <h1>示例2</h1>
  <div>
    <div>
      <Button size="big" theme="button">大大大</Button>
      <Button theme="button">普普普</Button>
      <Button size="small" theme="button">小小小</Button>
    </div>
    <div>
      <Button size="big" theme="link">大大大</Button>
      <Button theme="link">普普普</Button>
      <Button size="small" theme="link">小小小</Button>
    </div>
    <div>
      <Button size="big" theme="text">大大大</Button>
      <Button theme="text">普普普</Button>
      <Button size="small" theme="text">小小小</Button>
    </div>
  </div>
  <h1>示例3</h1>
  <div>
    <Button level="main">主要按钮</Button>
    <Button>普通按钮</Button>
    <Button level="danger">危险按钮</Button>
  </div>
  <div>
    <Button theme="link" level="main">主要链接按钮</Button>
    <Button theme="link" >普通链接按钮</Button>
    <Button theme="link" level="danger">危险链接按钮</Button>
  </div>
  <div>
    <Button theme="text" level="main">主要文字按钮</Button>
    <Button theme="text">普通文字按钮</Button>
    <Button theme="text" level="danger">危险文字按钮</Button>
  </div>
  <h1>示例4</h1>
  <Button disabled>禁用按钮</Button>
  <Button theme="link" disabled>禁用链接按钮</Button>
  <Button theme="link" disabled>禁用文字按钮</Button>
  <h1>示例5</h1>
  <Button :loading="true">加载中</Button>
  <Button>加载完毕</Button>
</template>
<script lang="ts">
import Button from '../lib/Button.vue';

export default {
  components: {Button},
  setup() {
    const onClick = ()=>{
      console.log('hi')
    }
    return {onClick}
  }
};
</script>
