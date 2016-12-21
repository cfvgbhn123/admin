<template>
  <div id="app">

        <router-view ></router-view>


        <router-view name='homedex'></router-view>

</div>
</template>

<script>
    export default {
        data() {
            return {
                msg: 'VUE 2.0 控制台'

            }
        },

        methods: {

        },
        components: {


        },
        mounted() {

        }
    }
</script>

<style lang="sass">
    @import "./sass/app.scss";
</style>