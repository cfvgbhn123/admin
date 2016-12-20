<template>
<div>
  <el-row :gutter="1" type="flex" justify="space-around">
  <el-col :span="24">
      <div class='info-all bg-purple-dark' >
          <div class="all-info">
              <img src="../assets/img/infoBar2.jpg" >
              <p>设备激活</p>
              <h1>{{DeviceNumber}}</h1>
          </div>
          <div class="all-info">
              <img src="../assets/img/infoBar1.jpg" >
              <p>新增玩家</p>
              <h1>{{NewPlayer}}</h1>
          </div>
          <div class="all-info">
              <img src="../assets/img/infoBar3.jpg" >
              <p>付费玩家</p>
              <h1>{{RmbPlayer}}</h1>
          </div>
          <div class="all-info">
              <img src="../assets/img/infoBar4.jpg" >
                <p>收入</p>
              <h1>{{GetMoney}}</h1>
          </div>
          <div></div>
          <div></div>
          <div></div>
          <div></div>
      </div>
  </el-col>
 
   
  
</el-row>
  <el-row :gutter="1" type="flex" justify="space-around">
  <el-col :span="24">
      <div class='info-online bg-purple-dark'>
          <PayRate></PayRate>
      </div>
  </el-col>
 
   
  
</el-row>
  <el-row :gutter="1" type="flex" justify="space-around">
  <el-col :span="24">
      <div class='info-important bg-purple-dark'>
          <AjaxDemo></AjaxDemo>
      </div>
  </el-col>
 

  
</el-row>
</div>
</template>
<script>
    import PayRate from "./chart/payrate.vue"
    import AjaxDemo from './chart/ajaxdemo.vue'
    export default {
        data() {
            return {
                Device: 0,
                DeviceNumber: 0,
                NewPlayer: 0,
                NewPlayerNumber: 0,
                RmbPlayer: 0,
                RmbPlayerNumber: 0,
                GetMoney: "￥" + 0.00,
                GetMoneyNumber: "￥" + 0,

            }
        },
        methods: {

        },
        components: {
            PayRate,
            AjaxDemo
        },
        mounted() {
            setTimeout(this.Device = 20000, 2000);
        },
        watch: {
            Device: function(newValue, oldValue) {
                var vm = this

                function animate(time) {
                    requestAnimationFrame(animate)
                    Tween.update(time)
                }
                new Tween.Tween({
                        tweeningNumber: oldValue
                    })
                    .easing(Tween.Easing.Quadratic.Out)
                    .to({
                        tweeningNumber: newValue
                    }, 500)
                    .onUpdate(function() {
                        vm.DeviceNumber = this.tweeningNumber.toFixed(0);
                        console.log(vm.DeviceNumber)
                    })
                    .start()
                animate()

            },

        }
    }
</script>
<style lang="sass" scoped>
    @import "../sass/Rightcontent.scss";
</style>