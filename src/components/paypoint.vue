<template>
    <div id="pay-point">
        <div id="pay-level">
            <div id="pay-level-title">
                <h3>付费等级</h3>
            </div>
            <el-tabs type="border-card" @tab-click='ReDraw'>
                <el-tab-pane label="付费金额">
                  <aside id="pay-money-chart">
                      
                  </aside>
                  <el-table
                        :data="tableData"
                        border
                        stripe
                        style="width: 100%">
                        <el-table-column
                        prop="level"
                        label="付费等级"
                        sortable
                        align="center">
                        </el-table-column>
                        <el-table-column
                        prop="data"
                        label="付费金额"
                        align="center"
                        sortable>
                        </el-table-column>
                </el-tab-pane>
                <el-tab-pane label="付费次数">
                   <aside id="pay-times-chart">
                      
                  </aside>
                  <el-table
                        :data="tableData"
                        border
                        stripe
                        style="width: 100%">
                        <el-table-column
                        prop="level"
                        label="付费等级"
                        sortable
                        align="center">
                        </el-table-column>
                        <el-table-column
                        prop="data"
                        label="付费次数"
                        align="center"
                        sortable>
                        </el-table-column>
                    </el-table>
                </el-tab-pane>
            </el-tabs>
        </div>
    </div>
</template>
<style lang="sass" scoped>
    @import "../sass/paypoint";
</style>
<script>
    export default {
        data() {
            return {
                tableData: [{
                    level: 33,
                    data: 10000
                }, {
                    level: 33,
                    data: 10000
                }, {
                    level: 33,
                    data: 10000
                }, {
                    level: 33,
                    data: 10000
                }, {
                    level: 33,
                    data: 10000
                }, ]
            };
        },
        methods: {
            ReDraw() {
                var categories = [33, 21, 34, 55, 6, 1, 8, 9, 11];
                var data = [66, 55, 33, 22, 22, 21, 11, 55, 22];
                console.log(this.tableData)
                for (var i = 0; i < this.tableData.length; i++) {
                    this.tableData[i].level = categories[i];
                    this.tableData[i].data = data[i];
                }
            }
        },
        mounted() {
            setTimeout(function() {
                $('#pay-money-chart').highcharts({
                    chart: {
                        type: 'column',
                        height: 360
                    },
                    title: {
                        text: ''
                    },
                    xAxis: {
                        title: {
                            text: '付费等级'
                        },
                        categories: [33, 21, 34, 55, 6, 1, 8, 9, 11],
                        crosshair: true
                    },
                    yAxis: {
                        min: 0,

                    },
                    plotOptions: {
                        column: {
                            pointPadding: 0.1,
                            borderWidth: 0
                        }
                    },
                    credits: {
                        enabled: false
                    },
                    series: [{
                        name: '￥付费金额',
                        data: [
                            10000, 8000, 5555, 3333, 2222, 2221, 1111, 555, 222
                        ],
                        showInLegend: false
                    }]
                })
                $('#pay-times-chart').highcharts({
                    chart: {
                        type: 'column',
                        width: $('#pay-money-chart').width(),
                        height: 360
                    },
                    title: {
                        text: ''
                    },
                    xAxis: {
                        title: {
                            text: '付费等级'
                        },
                        categories: [33, 21, 34, 55, 6, 1, 8, 9, 11],
                        crosshair: true
                    },
                    yAxis: {
                        min: 0,

                    },
                    plotOptions: {
                        column: {
                            pointPadding: 0.1,
                            borderWidth: 0
                        }
                    },
                    credits: {
                        enabled: false
                    },
                    series: [{
                        name: '付费次数',
                        data: [
                            66, 55, 33, 22, 22, 21, 11, 55, 22
                        ],
                        showInLegend: false
                    }]
                })
            }, 0)
        }

    }
</script>