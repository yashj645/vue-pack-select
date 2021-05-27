<template>
  <div class="no-internet-wrapper">
    <div class="no-internet-wrapper-text">
      <strong>You are not connected to internet</strong>
    </div>
  </div>
</template>

<script>
export default {
  setup () {
    

    return {}
  }
}
</script>

<style lang="scss" scoped>
  .no-internet-wrapper {
    height: 100vh;
    width: 100vw;
    background-color: #49668c;
    display: flex;
    align-items: center;
    justify-content: center;
    &-text {
      color: white;
    }
  }
</style>