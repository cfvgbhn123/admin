<template>
    <div id="new-player"  v-loading.body="loading">
        <div id="new-player-info">
            <div id="player-info-title">
                <h3>新增玩家</h3>
            </div>
            <el-tabs :active-name="activeName" type="card" @tab-click=ReDraw>
                <el-tab-pane label="新增与激活" name="新增与激活"></el-tab-pane>
                <el-tab-pane label="玩家转化率" name="玩家转化率"></el-tab-pane>
            </el-tabs>
            <aside>
                <div id="new-player-chart">
                    
                </div>
            </aside>
             <el-table
            
             v-if='tableData1.length'
                :data="tableData1"
                border
                stripe
                style="width: 100%">
                <el-table-column
                prop="date"
                label="日期"
                sortable
                align="center">
                </el-table-column>
                <el-table-column
                prop="series0"
                label="设备激活"
                align="center"
                >
                </el-table-column>
                 <el-table-column
                prop="series1"
                label="新增设备"
                align="center"
                >
                </el-table-column>
                 <el-table-column
                prop="series2"
                label="新增账户"
                align="center"
                >
                </el-table-column>
            </el-table>
            <el-table
            v-loading.body="loading"
            v-if="tableData2.length"
                :data="tableData2"
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
                >
                </el-table-column>
            </el-table>
        </div>
    </div>
</template>
<style lang=sass scoped>
    @import "../sass/newplayer.scss";
</style>
<script>
    export default {
        data() {
            return {
                loading: true,
                tableData1: [{
                    date: '一月',
                    series0: '11',
                    series2: '122'
                }],
                tableData2: [],
                activeName: '',
                新增与激活: {
                    categories: ['一月', '二月', '三月', '四月', '五月', '六月',
                        '七月', '八月', '九月', '十月', '十一月', '十二月'
                    ],
                    series: [{
                        name: '设备激活',
                        data: [7.0, 6.9, 9.5, 14.5, 18.2, 21.5, 25.2,
                            26.5, 23.3, 18.3, 13.9, 9.6
                        ]
                    }, {
                        name: '新增设备',
                        data: [-0.2, 0.8, 5.7, 11.3, 17.0, 22.0, 24.8,
                            24.1, 20.1, 14.1, 8.6, 2.5
                        ]
                    }, {
                        name: '新增账户',
                        data: [3.9, 4.2, 5.7, 8.5, 11.9, 15.2, 17.0,
                            16.6, 14.2, 10.3, 6.6, 4.8
                        ]
                    }]
                },
                玩家转化率: {
                    categories: ['一月', '二月', '三月', '四月', '五月', '六月',
                        '七月', '八月', '九月', '十月', '十一月', '十二月'
                    ],
                    series: [{
                        name: '转化率',
                        data: [
                            0.05, 0.03, 0.01, 0.06, 0.11, 0.33, 0.22
                        ]
                    }]
                }
            }
        },
        methods: {
            ReDraw(tab, event) {

                console.log(tab.name, event);
                var len = $('#new-player-chart').highcharts().series.length
                for (let i = 0; i < len; i++) {

                    $('#new-player-chart').highcharts().series[0].remove(false);
                    $('#new-player-chart').highcharts().redraw()
                }
                if (tab.name == '新增与激活') {
                    this.tableData1.push({
                        date: '一月'
                    })
                    this.tableData2.splice(0, this.tableData2.length)
                    var title = {
                        text: '新增与激活'
                    };

                    var xAxis = {
                        categories: this.新增与激活.categories
                    };
                    var yAxis = {
                        title: {
                            text: ''
                        },
                        plotLines: [{
                            value: 0,
                            width: 1,
                            color: '#808080'
                        }]
                    };

                    var tooltip = {
                        valueSuffix: ''
                    }

                    var legend = {
                        layout: 'vertical',
                        align: 'right',
                        verticalAlign: 'middle',
                        borderWidth: 0
                    };

                    var series = this.新增与激活.series;

                    var json = {};

                    json.title = title;
                    json.xAxis = xAxis;
                    json.yAxis = yAxis;
                    json.tooltip = tooltip;
                    json.legend = legend;
                    json.series = series;
                    $('#new-player-chart').highcharts(json);
                } else {
                    //切换表格数据
                    this.tableData1.splice(0, this.tableData1.length);
                    this.tableData2.push({
                        date: '一月'
                    })
                    var title = {
                        text: '玩家转化率'
                    };

                    var xAxis = {
                        categories: this.玩家转化率.categories
                    };
                    var yAxis = {
                        title: {
                            text: ''
                        },
                        plotLines: [{
                            value: 0,
                            width: 1,
                            color: '#808080'
                        }]
                    };

                    var tooltip = {
                        valueSuffix: ''
                    }

                    var legend = {
                        layout: 'vertical',
                        align: 'right',
                        verticalAlign: 'middle',
                        borderWidth: 0
                    };

                    var series = this.玩家转化率.series;

                    var json = {};

                    json.title = title;
                    json.xAxis = xAxis;
                    json.yAxis = yAxis;
                    json.tooltip = tooltip;
                    json.legend = legend;
                    json.series = series;
                    $('#new-player-chart').highcharts(json);
                }
            }
        },
        mounted() {
            //重设加载器
            this.loading = true;
            var _this = this
            setTimeout(function() {
                _this.loading = false;

            }, 1000)

            var title = {
                text: '新增与激活'
            };

            var xAxis = {
                categories: ['一月', '二月', '三月', '四月', '五月', '六月',
                    '七月', '八月', '九月', '十月', '十一月', '十二月'
                ]
            };
            var yAxis = {
                title: {
                    text: ''
                },
                plotLines: [{
                    value: 0,
                    width: 1,
                    color: '#808080'
                }]
            };

            var tooltip = {
                valueSuffix: ''
            }

            var legend = {
                layout: 'vertical',
                align: 'right',
                verticalAlign: 'middle',
                borderWidth: 0
            };

            var series = [{
                name: '设备激活',
                data: [7.0, 6.9, 9.5, 14.5, 18.2, 21.5, 25.2,
                    26.5, 23.3, 18.3, 13.9, 9.6
                ]
            }, {
                name: '新增设备',
                data: [-0.2, 0.8, 5.7, 11.3, 17.0, 22.0, 24.8,
                    24.1, 20.1, 14.1, 8.6, 2.5
                ]
            }, {
                name: '新增账户',
                data: [3.9, 4.2, 5.7, 8.5, 11.9, 15.2, 17.0,
                    16.6, 14.2, 10.3, 6.6, 4.8
                ]
            }];

            var json = {};

            json.title = title;
            json.xAxis = xAxis;
            json.yAxis = yAxis;
            json.tooltip = tooltip;
            json.legend = legend;
            json.series = series;

            $('#new-player-chart').highcharts(json);
        }
    }
</script>