<template>
    <div>
        <el-row :gutter="20">
            <el-col :span="8">
                <el-row :gutter="24" class="mgb20">
                    <el-col :span="12">
                        <el-card shadow="hover" :body-style="{padding: '0px'}">
                            <div class="grid-content grid-con-1">
                                <i class="el-icon-monitor grid-con-icon"></i>
                                <div class="grid-cont-right">
                                    <div class="grid-num">1234</div>
                                    <div>设备数</div>
                                </div>
                            </div>
                        </el-card>
                    </el-col>
                    <el-col :span="12">
                        <el-card shadow="hover" :body-style="{padding: '0px'}">
                            <div class="grid-content grid-con-2">
                                <i class="el-icon-video-play grid-con-icon"></i>
                                <div class="grid-cont-right">
                                    <div class="grid-num">321</div>
                                    <div>运行数</div>
                                </div>
                            </div>
                        </el-card>
                    </el-col>
                </el-row>
                <el-row :gutter="24" class="mgb20">
                    <el-col :span="12">
                        <el-card shadow="hover" :body-style="{padding: '0px'}">
                            <div class="grid-content grid-con-3">
                                <i class="el-icon-bell grid-con-icon"></i>
                                <div class="grid-cont-right">
                                    <div class="grid-num">5000</div>
                                    <div>故障数</div>
                                </div>
                            </div>
                        </el-card>
                    </el-col>
                    <el-col :span="12">
                        <el-card shadow="hover" :body-style="{padding: '0px'}">
                            <div class="grid-content grid-con-4">
                                <i class="el-icon-video-pause grid-con-icon"></i>
                                <div class="grid-cont-right">
                                    <div class="grid-num">5000</div>
                                    <div>待机数</div>
                                </div>
                            </div>
                        </el-card>
                    </el-col>
                </el-row>
                <el-card shadow="hover" style="height:460px;">
                    <div slot="header" class="clearfix">
                        <span>设备类型</span>
                    </div>
                    <div class="schart-box">
                        <!-- <div class="content-title">饼状图</div> -->
                        <schart class="schart" canvasId="pie" :options="options3"></schart>
                    </div>
                </el-card>
            </el-col>
            <el-col :span="16">
                <el-row :gutter="20" class="mgb20">
                     <el-col :span="24">
                    <el-card shadow="hover">
                        <schart ref="bar" class="schart" canvasId="bar" :options="options"></schart>
                    </el-card>
                    </el-col>
                </el-row>
                <el-row :gutter="20" class="mgb20">
                     <el-col :span="24">
                     <el-card shadow="hover">
                    <schart ref="line" class="schart" canvasId="line" :options="options2"></schart>
                     </el-card>
                     </el-col>
                </el-row>            
            </el-col>
        </el-row>
        <el-row>
             <el-card shadow="hover" style="height:412px;">
                    <div slot="header" class="clearfix">
                        <span>报警</span>
                        <!-- <el-button style="float: right; padding: 3px 0" type="text">添加</el-button> -->
                    </div>
                    <el-table :show-header="false" :data="todoList" style="width:100%;">
                        <el-table-column width="40">
                            <template slot-scope="scope">
                                <el-checkbox v-model="scope.row.status"></el-checkbox>
                            </template>
                        </el-table-column>
                        <el-table-column>
                            <template slot-scope="scope">
                                <div
                                    class="todo-item"
                                    :class="{'todo-item-del': scope.row.status}"
                                >{{scope.row.title}}</div>
                            </template>
                        </el-table-column>
                        <el-table-column width="200" align="center">
                            <template slot-scope="scope">
                                <!-- <i class="el-icon-edit"></i>
                                <i class="el-icon-delete"></i>-->
                                <span>{{scope.row.alarmTime}}</span>
                            </template>
                        </el-table-column>
                    </el-table>
                </el-card>
        </el-row>
       
    </div>
</template>

<script>
import Schart from 'vue-schart';
import bus from '../common/bus';
export default {
    name: 'dashboard',

    data() {
        return {
            name: localStorage.getItem('ms_username'),
            todoList: [
                {
                    title: '设备1温度过高',
                    status: false,
                    alarmTime: '2020-05-15 14:00:00'
                },
                {
                    title: '设备2温度过高',
                    status: true,
                    alarmTime: '2020-05-15 14:00:00'
                },
                {
                    title: '设备1断电',
                    status: false,
                    alarmTime: '2020-05-15 14:00:00'
                },
                {
                    title: '设备1故障',
                    status: false,
                    alarmTime: '2020-05-15 14:00:00'
                },
                {
                    title: '设备2故障',
                    status: true,
                    alarmTime: '2020-05-15 14:00:00'
                },
                {
                    title: '设备1故障',
                    status: false,
                    alarmTime: '2020-05-15 14:00:00'
                },
                {
                    title: '设备2故障',
                    status: true,
                    alarmTime: '2020-05-15 14:00:00'
                },
                {
                    title: '设备2故障',
                    status: true,
                    alarmTime: '2020-05-15 14:00:00'
                },
                {
                    title: '设备1故障',
                    status: false,
                    alarmTime: '2020-05-15 14:00:00'
                },
                {
                    title: '设备2故障',
                    status: true,
                    alarmTime: '2020-05-15 14:00:00'
                }
            ],

            options: {
                type: 'bar',
                title: {
                    text: '最近一周设备报警数'
                },
                xRorate: 25,
                labels: ['周一', '周二', '周三', '周四', '周五', '周六', '周日'],
                datasets: [
                    {
                        label: '干燥设备',
                        data: [2, 4, 1, 2, 3, 2, 1]
                    },
                    {
                        label: '液压设备',
                        data: [1, 3, 5, 2, 7, 1, 3]
                    },
                    {
                        label: '数控机床',
                        data: [6, 2, 8, 1, 5, 7, 2]
                    }
                ]
            },
            options2: {
                type: 'line',
                title: {
                    text: '开机率/故障率趋势图'
                },
                labels: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月'],
                datasets: [
                    {
                        label: '开机率',
                        data: [78, 4, 15, 65, 89]
                    },
                    {
                        label: '故障率',
                        data: [4, 2, 2, 6, 5]
                    }
                ]
            },
            options3: {
                type: 'pie',
                title: {
                    text: '设备种类饼状图'
                },
                legend: {
                    position: 'bottom'
                },
                bottomPadding:'10px',
                bgColor: '#fbfbfb',
                labels: ['干燥设备', '液压设备', '数控机床'],
                datasets: [
                    {
                        data: [334, 278, 190]
                    }
                ]
            }
        };
    },
    components: {
        Schart
    },
    computed: {
        role() {
            return this.name === 'admin' ? '超级管理员' : '普通用户';
        }
    },

    // created() {
    //     this.handleListener();
    //     this.changeDate();
    // },
    // activated() {
    //     this.handleListener();
    // },
    // deactivated() {
    //     window.removeEventListener('resize', this.renderChart);
    //     bus.$off('collapse', this.handleBus);
    // },
    methods: {
        // changeDate() {
        //     const now = new Date().getTime();
        //     this.data.forEach((item, index) => {
        //         const date = new Date(now - (6 - index) * 86400000);
        //         item.name = `${date.getFullYear()}/${date.getMonth() + 1}/${date.getDate()}`;
        //     });
        // }
        // handleListener() {
        //     bus.$on('collapse', this.handleBus);
        //     // 调用renderChart方法对图表进行重新渲染
        //     window.addEventListener('resize', this.renderChart);
        // },
        // handleBus(msg) {
        //     setTimeout(() => {
        //         this.renderChart();
        //     }, 200);
        // },
        // renderChart() {
        //     this.$refs.bar.renderChart();
        //     this.$refs.line.renderChart();
        // }
    }
};
</script>


<style scoped>
.el-row {
    margin-bottom: 20px;
}

.grid-content {
    display: flex;
    align-items: center;
    height: 100px;
}

.grid-cont-right {
    flex: 1;
    text-align: center;
    font-size: 14px;
    color: #999;
}

.grid-num {
    font-size: 30px;
    font-weight: bold;
}

.grid-con-icon {
    font-size: 50px;
    width: 100px;
    height: 100px;
    text-align: center;
    line-height: 100px;
    color: #fff;
}

.grid-con-1 .grid-con-icon {
    background: rgb(45, 140, 240);
}

.grid-con-1 .grid-num {
    color: rgb(45, 140, 240);
}

.grid-con-2 .grid-con-icon {
    background: rgb(100, 213, 114);
}

.grid-con-2 .grid-num {
    color: rgb(100, 213, 114);
}

.grid-con-3 .grid-con-icon {
    background: rgb(242, 94, 67);
}

.grid-con-3 .grid-num {
    color: rgb(242, 94, 67);
}
.grid-con-4 .grid-con-icon {
    background: rgb(241, 224, 90);
}

.grid-con-4 .grid-num {
    color: rgb(241, 224, 90);
}

.user-info {
    display: flex;
    align-items: center;
    padding-bottom: 20px;
    border-bottom: 2px solid #ccc;
    margin-bottom: 20px;
}

.user-avator {
    width: 120px;
    height: 120px;
    border-radius: 50%;
}

.user-info-cont {
    padding-left: 50px;
    flex: 1;
    font-size: 14px;
    color: #999;
}

.user-info-cont div:first-child {
    font-size: 30px;
    color: #222;
}

.user-info-list {
    font-size: 14px;
    color: #999;
    line-height: 25px;
}

.user-info-list span {
    margin-left: 70px;
}

.mgb20 {
    margin-bottom: 20px;
}

.todo-item {
    font-size: 14px;
}

.todo-item-del {
    text-decoration: line-through;
    color: #999;
}

.schart {
    width: 100%;
    height: 300px;
}
</style>
