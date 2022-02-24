<template>
  <div id="app">
    <myHeader/>
  </div>
</template>

<script>
import myHeader from './components/myHeader.vue'

export default {
  name: 'App',
  components: {
    myHeader,
  }
}
</script>

<style>
  @import "./assets/style/general.scss";
</style>
