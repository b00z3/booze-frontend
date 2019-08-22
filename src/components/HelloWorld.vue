<template>
    <el-col type="flex" justify="center">
      <div>
        <el-image style="width: 100px; height: 100px" :src="url" :fit="fit"></el-image>
      </div>
      <div>
        <h1>Ready to b00z3?</h1>
      </div>
  </el-col>
</template>

<script>
  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    },
    data() {
      return {
        test: '../assets/logo.png',
        fit: 'contain',
      }
    },
    computed: {
      url() {
        return require('../assets/logo.png')
      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1{
  margin:0.5em;
}
</style>