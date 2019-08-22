<template>
  <div id="app">
    <HelloWorld/>
    <team/>
    <api-call/>
    <el-backtop target=".page-component__scroll .el-scrollbar__wrap"></el-backtop>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ApiCall from './components/ApiCall.vue'
import Team from './components/Team.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    ApiCall,
    Team,
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
