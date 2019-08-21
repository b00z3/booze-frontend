<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/beer_emoji.png">
    <HelloWorld msg="Welcome to the awesome booze website!!!"/>
  <api-call/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ApiCall from './components/ApiCall.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    ApiCall,
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
img {
  width: 100px;
}
</style>
