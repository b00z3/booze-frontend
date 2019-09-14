<template>
    <div>
        <el-button
        class='give-margin'
        type="success"
        @click="analyze"
        round>Analyze!</el-button>
        <div v-show="predict">
            <h1>We predict... 👇</h1>
            <div v-loading="loading">
                <div v-for="sentence in res">
                    {{ sentence }}
                </div>
            </div>
        </div>
         <el-button
        class='give-margin'
        type="success"
        @click="analyze_iowa"
        round>Analyze with Iowa Data!</el-button>
        <div v-show="predict_iowa">
            <h1>We predict... 👇</h1>
            <div v-loading="loading_iowa">
                <div v-for="sentence in iowa_res">
                    {{ sentence }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: 'api-call',
        data() {
            return {
                res: ['🤔'],
                iowa_res:  ['🤔'],
                predict: false,
                predict_iowa: false,
                loading: true,
                loading_iowa: true,
            }
        },
        props: {
            team: {
                type: Array,
                default: []
            },
        },
        methods: {
            analyze() {
                this.predict = true
                this.loading = true
                axios
                    .post('https://b00z3.herokuapp.com/',
                           this.team)
                    .then(response => {
                        this.res = response.data.answer
                        this.loading = false
                    })
                    .catch(error => {
                        console.log(error)
                        this.res = 'Error retrieving data'
                        this.loading = false
                    })
            },
            analyze_iowa() {
                this.predict_iowa = true
                this.loading_iowa = true
                axios
                    .post('https://b00z3.herokuapp.com/iowa',
                           this.team)
                    .then(response => {
                        this.iowa_res = response.data.answer
                        this.loading_iowa = false
                    })
                    .catch(error => {
                        console.log(error)
                        this.res = ['Error retrieving data']
                        this.loading_iowa = false
                    })
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>