<template>
    <div>
            <div id="jump-player"  v-loading.body="loading">
                <div id="jump-player-info">
                    <div id="player-info-title">
                        <h3>活跃玩家</h3>
                    </div>
                    <el-tabs :active-name="activeName" type="card" @tab-click=''>
                        <el-tab-pane label="新增与激活" name="新增与激活"></el-tab-pane>
                        <el-tab-pane label="玩家转化率" name="玩家转化率"></el-tab-pane>
                    </el-tabs>
                    <aside>
                        <div id="jump-player-chart">
                            
                        </div>
                    </aside>
               
                </div>
            </div>
    </div>
</template>
<style lang="sass" scoped>
    @import '../sass/jumpplayer.scss';
</style>
<script>
    export default {
        data() {
            return {
                activeName: ''
            }
        }
    }
</script>