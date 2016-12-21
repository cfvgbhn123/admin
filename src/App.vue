<template>
  <div id="app">

        <router-view ></router-view>


        <router-view name='homedex'></router-view>
     

</div>
</template>

<script>
    import toast from './components/chart/filter.vue'
    export default {
        data() {
            return {
                msg: true,

            }
        },

        methods: {
            toast() {
                console.log(this.msg)
                this.msg = !(this.msg);
            }
        },
        components: {

            toast
        },
        mounted() {
            var _this = this;
            Event.$on('callTaost', function() {
                alert(1);
            })
        }
    }
</script>

<style lang="sass">
    @import "./sass/app.scss";
</style>