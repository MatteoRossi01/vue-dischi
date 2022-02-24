<template>
  <div id="app">
    <myHeader/>
    <myMain/>
  </div>
</template>

<script>
import myHeader from './components/myHeader.vue'
import myMain from './components/myMain.vue'

export default {
  name: 'App',
  components: {
    myHeader,
    myMain,
  }
}
</script>

<style>
  @import "./assets/style/general.scss";
</style>
