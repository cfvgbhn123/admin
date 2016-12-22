<template>
<div>
    <p  >{{Bdata}}</p>
    <input type="number" v-model="Adata[0][1]"step="22">
    <input type="number" v-model="Adata[1][1]"step="22">
    <input type="number" v-model="Adata[2][1]"step="22">
    <input type="number" v-model="Adata[3][1]"step="22">
    <input type="number" v-model="Adata[4][1]"step="22">
    <input type="number" v-model="Adata[5][1]"step="22">
    <div id="welcom"  style="width:100%;height:100%;background-color:darkcyan">
    
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
                Bdata: '测试',
            }
        },
        methods: {
            change() {
                // this.Adata[0][1] = this.Adata[0][1] + 1000;
                // console.log(this.Adata)
                // var _this = this;
                // _this.Bdata = cloneObj(_this.Adata)
                // $('#welcom').highcharts().series[0].setData(_this.Bdata);

                // function cloneObj(obj) {
                //     var str, newobj = obj.constructor === Array ? [] : {};
                //     if (typeof obj !== 'object') {
                //         return;
                //     } else if (window.JSON) {
                //         str = JSON.stringify(obj), //系列化对象
                //             newobj = JSON.parse(str); //还原
                //     } else {
                //         for (var i in obj) {
                //             newobj[i] = typeof obj[i] === 'object' ?
                //                 cloneObj(obj[i]) : obj[i];
                //         }
                //     }
                //     return newobj;
                // }

                // if (!(data == backup)) {
                //     _this.Bdata = cloneObj(_this.Adata);
                //     $target.highcharts().series[0].setData(_this.Bdata);
                //     _this.Bdata = _this.Adata;
                //     unbind();
                //     HotChange(backup, data, $target);
                // } else if (data == backup) {
                //     _this.Adata = cloneObj(_this.Bdata);
                //     $target.highcharts().series[0].setData(_this.Adata);
                //     _this.Adata = _this.Bdata;
                //     unbind();
                //     HotChange(backup, data, $target);
                // }


            },

        },
        // watch: {
        //     Adata: {
        //         handler: function(val, oldVal) {
        //             console.log(val, oldval)
        //         },
        //         deep: true
        //     }
        // },
        mounted() {
            var _this = this;
            HotChange('Adata', 'Bdata', $('#welcom'));
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

            function HotChange(data, backup, $target) {
                var unbind = _this.$watch(data, function() {
                    if (!(data == backup)) {
                        _this.Bdata = cloneObj(_this.Adata);
                        $target.highcharts().series[0].setData(_this.Bdata);
                        _this.Bdata = _this.Adata;
                        unbind();
                        HotChange(backup, data, $target);
                    } else if (data == backup) {
                        _this.Adata = cloneObj(_this.Bdata);
                        $target.highcharts().series[0].setData(_this.Adata);
                        _this.Adata = _this.Bdata;
                        unbind();
                        HotChange(backup, data, $target);
                    }

                });
            }


            //   console.log(this._watchers[1])


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