<template>
  <el-row type="flex" class="row-bg" justify="center">
    <el-col :span="6">
      <el-container>
          <h1>Ready to b00z3?</h1>
          <el-image style="width: 100px; height: 100px" :src="url" :fit="fit"></el-image>
      </el-container>
    </el-col>
  </el-row>
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
  h3 {
    margin: 40px 0 0;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin: 0 10px;
  }

  a {
    color: #42b983;
  }
</style>