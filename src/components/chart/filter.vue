<template>
         <div id="filter-wrap">
             
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
                        @input="searchGame"
                        >
                        </el-input>
                </div>
                <div id="filter-check">
                    <el-button type="primary" size="mini" @click=pickAll>全选</el-button>
                    <el-button type="primary" size="mini" @click=dispickChoose>反选</el-button>
                </div>
                <div id="filter-table">
                   <el-checkbox-group v-model="checkList">
                        <el-checkbox :label=check.game v-if="check.key" v-for="check in checkall " ></el-checkbox>
                        
                    </el-checkbox-group>
                </div>
                <div id="filter-footer">
                    <el-button type="primary" size="small"@click='pushChoose(checkList)'>确定</el-button>
                    <el-button type="primary" size="small" @click='closefilter'>取消</el-button>
                </div>
            </div>
     </div>

        
</template>
<script>
    export default {
        mounted() {
            this.$watch('input2', function() {
                for (var i = 0; i < this.checkall.length; i++) {
                    if (this.checkall[i].game.search(this.input2) < 0) {
                        this.checkall[i].key = false;
                    } else {
                        this.checkall[i].key = true;
                    }
                }
            })
        },
        methods: {
            searchGame() {
                console.log(this.$http)
            },
            //关掉筛选界面
            closefilter() {
                Event.$emit('closefilter')
            },
            //广播筛选成功事件 推送筛选数据
            pushChoose() {
                var _this = this;
                Event.$emit('pushChoose', _this.checkList)
            },
            //全选筛选列表
            pickAll() {
                this.checkList.splice(0, this.checkList.length)
                for (var i = 0; i < this.checkall.length; i++) {
                    this.checkList.push(this.checkall[i].game)
                }
            },
            //同上 反选
            dispickChoose() {
                var temp = [];
                var a = [];
                for (var i = 0; i < this.checkall.length; i++) {
                    temp.push(this.checkall[i].game)
                }
                for (var j = 0; j < this.checkall.length; j++) {
                    var b = temp[j];
                    if (this.checkList.indexOf(b) == -1) {
                        a.push(b);
                    }
                }
                this.checkList = a

            },

        },
        data() {
            return {
                input2: '',
                gameFlag: true,
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
                multipleSelection: [],
                checkall: [{
                    game: '一区',
                    key: true
                }, {
                    game: '二区',
                    key: true
                }, {
                    game: '三区',
                    key: true
                }, {
                    game: '四区',
                    key: true
                }],
                checkList: []
            }
        }
    }
</script>
<style lang="sass" scoped>
    @import '../../sass/filter.scss';
</style>