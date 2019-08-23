<template>
  <div id="app">
    <HelloWorld/>
    <team/>
    <footer-beer/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Team from './components/Team.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Team,
    'footer-beer': Footer,
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
  margin-bottom: 0%;
}
.el-footer {
    color: #333;
    text-align: center;
    line-height: 60px;
    margin-top: 10em;
  }
</style>
