<template>
<div>
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
@import url("https://fonts.googleapis.com/icon?family=Material+Icons");
@import url("https://fonts.googleapis.com/css?family=Open+Sans:300,400|Hind:300,400|Noto+Sans+JP:300,400&display=swap");
* {
  margin: 0;
  padding: 0;
}
</style>
