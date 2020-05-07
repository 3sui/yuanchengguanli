<!--
 * @Author: your name
 * @Date: 2020-05-07 13:46:11
 * @LastEditTime: 2020-05-07 14:14:14
 * @LastEditors: Please set LastEditors
 * @Description: 报警记录
 * @FilePath: \vue-manage-system\src\components\view\AlarmRecord.vue
 -->
<!--  -->
<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-lx-cascades"></i> 报警记录
                </el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="container">
            <div class="handle-box">
                <el-row>
                    <el-col :span="18">
                        <div class="product-status">
                            <el-input
                                v-model="query.name"
                                placeholder="请输入关键字"
                                class="handle-input mr10"
                            ></el-input>
                            <el-select
                                v-model="query.address"
                                placeholder="设备种类"
                                class="handle-select mr10"
                            >
                                <el-option key="1" label="干燥设备" value="干燥设备"></el-option>
                            </el-select>
                            <el-select
                                v-model="query.address"
                                placeholder="工作状态"
                                class="handle-select mr10"
                            >
                                <el-option key="1" label="运行中" value="运行中"></el-option>
                            </el-select>
                            <el-select
                                v-model="query.address"
                                placeholder="开关机"
                                class="handle-select mr10"
                            >
                                <el-option key="1" label="开机" value="开机"></el-option>
                            </el-select>
                            <el-date-picker
                                class="mr10"
                                v-model="value2"
                                type="daterange"
                                align="right"
                                unlink-panels
                                range-separator="至"
                                start-placeholder="开始日期"
                                end-placeholder="结束日期"
                                :picker-options="pickerOptions"
                            ></el-date-picker>
                            <el-button type="primary" icon="el-icon-search" @click="handleSearch">搜索</el-button>
                        </div>
                    </el-col>
                </el-row>
                <el-table
                    :data="tableData"
                    border
                    class="table"
                    ref="multipleTable"
                    header-cell-class-name="table-header"
                    @selection-change="handleSelectionChange"
                >
                    <!-- <el-table-column type="selection" width="55" align="center"></el-table-column> -->
                    <el-table-column prop="id" label="序号" width="55" align="center"></el-table-column>
                    <el-table-column prop="name" label="设备ID"></el-table-column>
                    <el-table-column prop="name" label="设备种类"></el-table-column>
                    <el-table-column prop="name" label="设备名称"></el-table-column>

                    <el-table-column prop="name" label="型号描述"></el-table-column>
                    <el-table-column prop="name" label="出厂编号"></el-table-column>
                    <el-table-column prop="name" label="测点名称"></el-table-column>
                    <el-table-column prop="name" label="上限值"></el-table-column>
                    <el-table-column prop="name" label="下限值"></el-table-column>
                    <el-table-column prop="name" label="报警值"></el-table-column>
                    <el-table-column prop="name" label="最近报警日期"></el-table-column>
                    <el-table-column prop="name" label="报警次数"></el-table-column>
                </el-table>
            </div>
        </div>
    </div>
</template>

<script>
import { fetchData } from '../../api/index';

export default {
    name: 'AlarmRecord',
    data() {
        return {
            tableData: [],
            query: {
                address: '',
                name: '',
                pageIndex: 1,
                pageSize: 10
            },
            multipleSelection: [],
            value1: '',
            value2: '',
            pickerOptions: {
                shortcuts: [
                    {
                        text: '最近一周',
                        onClick(picker) {
                            const end = new Date();
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
                            picker.$emit('pick', [start, end]);
                        }
                    },
                    {
                        text: '最近一个月',
                        onClick(picker) {
                            const end = new Date();
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
                            picker.$emit('pick', [start, end]);
                        }
                    },
                    {
                        text: '最近三个月',
                        onClick(picker) {
                            const end = new Date();
                            const start = new Date();
                            start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
                            picker.$emit('pick', [start, end]);
                        }
                    }
                ]
            }
        };
    },

    components: {},

    computed: {},
    created() {
        this.getData();
    },
    methods: {
        getData() {
            fetchData(this.query).then(res => {
                console.log(res);
                this.tableData = res.list;
                this.pageTotal = res.pageTotal || 50;
            });
        },
        handleSearch() {
            this.$set(this.query, 'pageIndex', 1);
            this.getData();
        },
        handleSelectionChange(val) {
            this.multipleSelection = val;
        }
    }
};
</script>
<style scoped>
.product-status {
    margin-bottom: 10px;
    display: flex;
    justify-content: space-between;
}
.mt-10 {
    margin-bottom: 10px;
}
.mr10 {
    margin-right: 10px;
}
</style>