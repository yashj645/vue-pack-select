<template>
  <div :class="['bottom-button', selected ? 'bottom-button-selected' : 'bottom-button-not-selected']">
    <slot></slot>
  </div>
</template>
<script>
export default {
  props: {
    selected: {
      type: Boolean,
      default: false
    }
  },
  setup () {
    return {
    }
  }
}
</script>

<style lang="scss" scoped>
  .bottom-button {
    width: 100%;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }
  .bottom-button-selected {
    background: #d95a00;
    color: white;
    &:hover {
      background: #fcd292;
    }
  }
  .bottom-button-not-selected {
    border: 1px solid #d95a00;
    color: #d95a00;
    &:hover {
      background: #ededed;
    }
  }
</style>
