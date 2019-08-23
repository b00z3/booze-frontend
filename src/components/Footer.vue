<template>
    <el-footer>
        <div> Made with 🍺 for <a href="7gate.academy">7gate</a> </div>
        <div>
        By
            <a :href="rory_url">Rory, </a>
            <a :href="sina_url">Sina, </a>
        and <a :href="parsa_url">Parsa</a>
        </div>
    </el-footer>
</template>

<script>
    export default {
        name: 'footer-beer',
        data() {
            return {
                sina_url: 'http://sinakhalili.com',
                parsa_url: '',
                rory_url: '',
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>