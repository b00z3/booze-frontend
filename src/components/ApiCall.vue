<template>
    <div>
        <p>==============</p>
        {{ something }}
        <p>==============</p>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        name: 'api-call',
        data() {
            return {
                something: 'value'
            }
        },
        created() {
            axios
            .get('https://b00z3.herokuapp.com/')
            .then(response => (this.something = response.data))
        }
    }
</script>

<style lang="scss" scoped>

</style>