<template>
  <div id="app">

        <router-view ></router-view>


        <router-view name='homedex'></router-view>
     
         <filterBox v-if=filterFlag></filterBox>
    
</div>
</template>

<script>
    import filterBox from './components/chart/filter.vue'
    export default {
        data() {
            return {
                filterFlag: false,

            }
        },

        methods: {
            toast() {
                console.log(this.msg)
                this.msg = !(this.msg);
            }
        },
        components: {

            filterBox
        },
        mounted() {
            var _this = this;
            Event.$on('callfilter', function() {
                _this.filterFlag = !(_this.filterFlag)
            })
            Event.$on('closefilter', function() {
                _this.filterFlag = false
            })
            Event.$on('pushChoose', function() {
                _this.filterFlag = false
            })
        }
    }
</script>

<style lang="sass">
    @import "./sass/app.scss";
</style>