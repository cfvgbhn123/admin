<template>
<div>
    <input type="text" name="" v-model="anfan"value="">
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
                anfan: 3000,
                w37: 4563,
                w4399: 6546,
                w5399: 3453,
                w9377: 3243,
                qq: 555,

            }
        },
        mounted() {
            var _this = this;
            this.$watch('anfan', function() {
                $('#welcom').highcharts().series[0].setData([
                    ['安锋游戏', _this.anfan],
                    ['37玩', _this.w37],
                    ['4399', _this.w4399],
                    ['琳琅天上', _this.qq],
                    ['9377', _this.w9377],
                    ['5399', _this.w5399]
                ])
            })

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
                        data: [
                            ['安锋游戏', _this.anfan],
                            ['37玩', _this.w37],
                            ['4399', _this.w4399],
                            ['琳琅天上', _this.qq],
                            ['9377', _this.w9377],
                            ['5399', _this.w5399]
                        ]
                    }]
                });
            });

        }
    }
</script>