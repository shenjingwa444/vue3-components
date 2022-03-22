<template>
  <button class="pixu-button" :class=" classes " :disabled="disabled">
    <slot/>
  </button>
</template>

<script lang="ts">
import {computed} from 'vue';

export default {
  props: {
    theme: {
      type: String,
      default: 'button',
    },
    size: {
      type: String,
    },
    level: {
      type: String,
      default: 'normal'
    },
    disabled:{
      type:Boolean,
      default:false,
    }
  },
  setup(props) {
    const {theme, size, level,} = props;
    const classes = computed(() => {
      return {
        [`pixu-theme-${theme}`]: theme,
        [`pixu-size-${size}`]: size,
        [`pixu-level-${level}`]: level,
      };
    });
    return {classes};
  }
};
</script>

<style lang="scss">
$h: 32px;
$border-color: #d9d9d9;
$color: #333;
$blue: #40a9ff;
$radius: 4px;
$red:red;
$gray:gray;
.pixu-button {
  height: $h;
  padding: 0 12px;
  cursor: pointer;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  white-space: nowrap;
  background-color: white;
  color: $color;
  border: 1px solid $border-color;
  border-radius: $radius;
  box-shadow: 0 1px 0 fade-out(black, 0.95);
  transition: background 250ms;

  & + & {
    margin-left: 8px;
  }
  &:focus, &:hover {
    color: $blue;
    border-color: $blue;
  }
  &:focus {
    outline: none
  }
  &::-moz-focus-inner {
    border: 0;
  }
  &.pixu-theme-link {
    border-color: transparent;
    box-shadow: none;
    color: $blue;
    &:hover, &:focus {
      color: lighten($blue, 10%);
    }
  }
  &.pixu-theme-text {
    border-color: transparent;
    box-shadow: none;
    color: inherit;

    &:hover, &:focus {
      background: darken(white, 5%);
    }
  }
  &.pixu-size-big {
    font-size: 24px;
    height: 48px;
    padding: 0 16px;
  }
  &.pixu-size-small {
    font-size: 12px;
    height: 20px;
    padding: 0 4px;
  }
  &.pixu-theme-button {
    &.pixu-level-main {
      background-color: $blue;
      color: white;
      border-color: $blue;
      &:hover, &:focus {
        background: darken($blue, 10%);
        border-color: darken($blue, 10%)
      }
    }
    &.pixu-level-danger {
      background-color: $red;
      border-color: $red;
      color: white;

      &:hover, &:focus {
        background-color: darken($red, 10%);
        border-color: darken($red, 10%);
      }
    }
  }
  &.pixu-theme-link{
    &.pixu-level-danger{
      color: $red;
      &:hover,&:focus{
        color:darken($red,10%);
      }
    }
  }
  &.pixu-theme-text{
    &.pixu-level-main{
      color:$blue;
      &:hover,&:focus{
        color:darken($blue,10%)
      }
    }
    &.pixu-level-danger{
      color:$red;
      &:hover,&:focus{
        color:darken($red,10%)
      }
    }
  }
  &.pixu-theme-button{
    &[disabled]{
      cursor:not-allowed;
      color:$gray;
      &:hover{
        border-color:$gray;
      }
    }
  }
  &.pixu-theme-link,&.pixu-theme-text{
    &[disabled]{
      cursor:not-allowed;
      color:$gray;
    }
  }
}
</style>