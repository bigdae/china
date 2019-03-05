<template>
  <div id="app">
    <China msg="Welcome to Your Vue.js App"/>
    <English/>
  </div>
</template>

<script>
import China from './components/China.vue'
import English from './components/English.vue'

export default {
  name: 'app',
  components: {
    China, English
  }
}
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
   