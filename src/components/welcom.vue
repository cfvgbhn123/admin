<template>
<div>
    <p>{{Adata}}</p>
    <input type="number" v-model="Adata[0][1]"step="22">
    <input type="number" v-model="Adata[1][1]"step="22">
    <input type="number" v-model="Adata[2][1]"step="22">
    <input type="number" v-model="Adata[3][1]"step="22">
    <input type="number" v-model="Adata[4][1]"step="22">
    <input type="number" v-model="Adata[5][1]"step="22">
    <div id="welcom" style="width:100%;height:100%;background-color:darkcyan">
    
</div>
</div>

</template>

<style scoped lang="sass">
    @import "../sass/common.scss";
</style>

<script>
    export default {
        data() {
            return {
                Adata: [
                    ['安锋游戏', 999],
                    ['37玩', 999],
                    ['4399', 888],
                    ['琳琅天上', 999],
                    ['9377', 999],
                    ['5399', 999]
                ],
                temp: null

            }
        },
        methods: {
            change() {



            }
        },
        mounted() {
            var _this = this;
            binder('Adata');
            var cloneObj = function(obj) {
                var str, newobj = obj.constructor === Array ? [] : {};
                if (typeof obj !== 'object') {
                    return;
                } else if (window.JSON) {
                    str = JSON.stringify(obj), //系列化对象
                        newobj = JSON.parse(str); //还原
                } else {
                    for (var i in obj) {
                        newobj[i] = typeof obj[i] === 'object' ?
                            cloneObj(obj[i]) : obj[i];
                    }
                }
                return newobj;
            };

            function binder(target) {
                var unbind = _this.$watch(target, function() {

                    if (target == 'Adata') {
                        _this.temp = cloneObj(_this.Adata);

                        $('#welcom').highcharts().series[0].setData(_this.temp);

                        unbind();
                        console.log(_this._watchers);
                        binder('temp')

                    } else if (target == 'temp') {
                        _this.Adata = cloneObj(_this.temp);

                        $('#welcom').highcharts().series[0].setData(_this.Adata);

                        unbind();
                        console.log(_this._watchers);
                        binder('Adata')
                    }

                });
            }


            console.log(this._watchers[1])


            $(function() {
                $('#welcom').highcharts({
                    chart: {
                        plotBackgroundColor: null,
                        plotBorderWidth: null,
                        plotShadow: false
                    },
                    title: {
                        text: ' 2016年手游市场份额'
                    },
                    tooltip: {
                        pointFormat: '{series.name}: <b>{point.percentage:.1f}%</b>'
                    },
                    plotOptions: {
                        pie: {
                            allowPointSelect: true,
                            cursor: 'pointer',
                            dataLabels: {
                                enabled: true,
                                format: '<b>{point.name}</b>: {point.percentage:.1f} %',
                                style: {
                                    color: (Highcharts.theme && Highcharts.theme.contrastTextColor) || 'black'
                                }
                            }
                        }
                    },
                    series: [{
                        type: 'pie',
                        name: '市场占有率',
                        data: _this.Adata
                    }]
                });
            });

        }
    }
</script>