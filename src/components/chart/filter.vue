<template>
    
            <div id="filter-box" >
                <div id="filter-title">
                   <span>筛选</span>
                   <i class="el-icon-close" @click='closefilter'></i>
                </div>
                <div id="filter-block">
                        <el-button :plain="true" type="success">版本</el-button>
                        <el-button :plain="true" type="warning">区服</el-button>
                        <el-input
                        placeholder="搜索"
                        icon="search"
                        v-model="input2"
                        >
                        </el-input>
                </div>
                <div id="filter-check">
                    <el-button type="primary" size="mini">全选</el-button>
                    <el-button type="primary" size="mini">反选</el-button>
                </div>
                <div id="filter-table">
                      <el-table
                        :data="tableData3"
                        border
                        style="width: 100%"
                        >
                        <el-table-column
                        type="selection"
                        width="55">
                        </el-table-column>
                        <el-table-column
                        inline-template
                        label="日期"
                        width="120">
                        <div>{{ row.date }}</div>
                        </el-table-column>
                        <el-table-column
                        prop="name"
                        label="姓名"
                        width="120">
                        </el-table-column>
                        <el-table-column
                        prop="address"
                        label="地址"
                        show-overflow-tooltip>
                        </el-table-column>
                    </el-table>
                </div>
                <div id="filter-footer">
                    <el-button type="primary" size="small">确定</el-button>
                    <el-button type="primary" size="small">取消</el-button>
                </div>
            </div>
        
</template>
<script>
    export default {
        methods: {
            closefilter() {
                Event.$emit('closefilter')
            }
        },
        data() {
            return {
                tableData3: [{
                    date: '2016-05-03',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1518 弄'
                }, {
                    date: '2016-05-02',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1518 弄'
                }, {
                    date: '2016-05-04',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1518 弄'
                }, {
                    date: '2016-05-01',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1518 弄'
                }, {
                    date: '2016-05-08',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1518 弄'
                }, {
                    date: '2016-05-06',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1518 弄'
                }, {
                    date: '2016-05-07',
                    name: '王小虎',
                    address: '上海市普陀区金沙江路 1518 弄'
                }],
                multipleSelection: []
            }
        }
    }
</script>
<style lang="sass" scoped>
    @import '../../sass/filter.scss';
</style>