<template>
  <div>
    <button class="pixu-switch" :class="{'pixu-checked':value}" @click="toggle">
      <span></span>
    </button>
  </div>
</template>

<script lang="ts">

export default {
  props: {
    value: Boolean,
  },
  setup(props, context) {
    const toggle = () => {
      context.emit('update:value', !props.value);
    };
    return {toggle};
  }
};
</script>

<style lang="scss">
$h: 22px;
$h2: $h - 4px;
.pixu-switch {
  height: $h;
  width: $h*2;
  background: gray;
  border: none;
  border-radius: $h/2;
  position: relative;

  > span {
    position: absolute;
    top: 2px;
    left: 2px;
    height: $h2;
    width: $h2;
    background: white;
    border-radius: $h2/2;
    transition: all 1s;
  }

  &.pixu-checked {
    background: blue;

  }

  &.pixu-checked > span {
    left: calc(100% - #{$h2} - 2px)
  }

  &:focus {
    outline: none;
  }

  &:active {
    > span {
      width: $h2 + 4px;
    }
  }

  &.pixu-checked:active {
    > span {
      width: $h2 + 4px;
      margin-left: -4px;
    }
  }
}


</style>