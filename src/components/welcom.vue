<template>

<div id="welcom" style="width:100%;height:100%;background-color:darkcyan">
    
</div>
</template>

<style scoped lang="sass">
    @import "../sass/common.scss";
</style>

<script>
    export default {
        data() {
            return {

            }
        },
        mounted() {
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
                        name: 'Browser share',
                        data: [
                            ['安锋游戏', 45.0],
                            ['37玩', 26.8], {
                                name: 'Chrome',
                                y: 12.8,
                                sliced: true,
                                selected: true
                            },
                            ['琳琅天上', 8.5],
                            ['9377', 6.2],
                            ['5399', 0.7]
                        ]
                    }]
                });
            });

        }
    }
</script>