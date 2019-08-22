<template>
    <div>
        <el-row>
            <el-col>
                <div class="helptext"> To get started, click the button below and add member to your party </div>
            </el-col>
        </el-row>
        <el-row>
            <el-col :xs="12" :sm="6" :md="4" :lg="3" :xl="1" v-for="person in people" :key="person.id">
                <el-card class="box-card">
                    <div>Age: {{person.age}}</div>
                    <div>Married? {{person.married}}</div>
                    <div>Gender: {{person.gender}}</div>
                </el-card>
            </el-col>
        </el-row>
        <el-button class='give-margin' type="primary" icon="el-icon-circle-plus" circle></el-button>
        <el-button class='give-margin' type="success" round>Analyze!</el-button>

    </div>
</template>

<script>
    export default {
        name: 'team',
        data() {
            return {
                people: [{
                    'age': 21,
                    'married': false,
                    'gender': 'male',
                },
                {
                    'age': 21,
                    'married': false,
                    'gender': 'male',
                },
                {
                    'age': 21,
                    'married': false,
                    'gender': 'male',
                },
                {
                    'age': 21,
                    'married': false,
                    'gender': 'male',
                }]
            }
        },
    }
</script>

<style scoped>
    .helptext {
        margin: 3em
    }
      .text {
    font-size: 14px;
  }

  .item {
    padding: 18px 0;
  }

  .box-card {
    margin: 1%;
  }
  .give-margin {
      margin:1em
  }
</style>