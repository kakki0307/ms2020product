<template>
  <div id="app">
    <index />
    <router-view />
  </div>
</template>

<script>
import Vue from 'vue'
import Index from './components/Index.vue'

export default Vue.extend({
  name: 'app',
  components: {
    Index
  }
})
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
