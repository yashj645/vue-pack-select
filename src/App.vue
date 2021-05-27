<template>
  <div id="app">
    <main-page></main-page>
  </div>
</template>

<script>
import { ref, onMounted, watchEffect } from 'vue'
import MainPage from './Pages/MainPage.vue'
export default {
  name: 'App',
  components: {
    MainPage
  },
  setup () {
    return {
    }
  }
}
</script>

<style>
</style>
