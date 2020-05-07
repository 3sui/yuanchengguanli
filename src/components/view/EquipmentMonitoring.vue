<!--
 * @Author: your name
 * @Date: 2020-05-06 16:21:18
 * @LastEditTime: 2020-05-07 10:50:08
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \vue-manage-system\src\components\view\EquipmentMonitoring.vue
 -->
<!--  -->
<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-lx-cascades"></i> 设备监控
                </el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="container">
            <div class="handle-box">
                <el-row>
                    <el-col :span="6">
                        <div class="mt-10">
                            <el-button
                                type="primary"
                                icon="el-icon-delete"
                                class="handle-del mr10"
                                @click="delAllSelection"
                            >新增</el-button>
                        </div>
                        <div>
                            <el-button
                                type="primary"
                                icon="el-icon-delete"
                                class="handle-del mr10"
                                @click="delAllSelection"
                            >批量删除</el-button>
                        </div>
                    </el-col>
                    <el-col :span="18">
                        <div style="text-align: right">
                            <el-button
                                type="primary"
                                icon="el-icon-delete"
                                class="handle-del mt-10"
                                @click="visible = true;"
                            >阈值查看</el-button>
                        </div>

                        <el-dialog
                            v-dialogDrag
                            title="阈值详情"
                            center
                            :visible.sync="visible"
                            width="30%"
                        >
                            <div>
                                <table>
                                    <thead>
                                        <tr>
                                            <th>测点名称</th>
                                            <th>上限值</th>
                                            <th>下限值</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr>
                                            <td>主机温度</td>
                                            <td>234</td>
                                            <td>123</td>
                                        </tr>
                                        <tr>
                                            <td>主机温度</td>
                                            <td>234</td>
                                            <td>123</td>
                                        </tr>
                                        <tr>
                                            <td>主机温度</td>
                                            <td>234</td>
                                            <td>123</td>
                                        </tr>
                                        <tr>
                                            <td>主机温度</td>
                                            <td>234</td>
                                            <td>123</td>
                                        </tr>
                                        <tr>
                                            <td>主机温度</td>
                                            <td>234</td>
                                            <td>123</td>
                                        </tr>
                                        <tr>
                                            <td>主机温度</td>
                                            <td>234</td>
                                            <td>123</td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                            <span slot="footer" class="dialog-footer">
                                <!-- <el-button @click="visible = false">取 消</el-button> -->
                                <el-button type="primary" @click="visible = false">确 定</el-button>
                            </span>
                        </el-dialog>
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
            </div>
            <el-table
                :data="tableData"
                border
                class="table"
                ref="multipleTable"
                header-cell-class-name="table-header"
                @selection-change="handleSelectionChange"
            >
                <el-table-column type="selection" width="55" align="center"></el-table-column>
                <el-table-column prop="id" label="序号" width="55" align="center"></el-table-column>

                <el-table-column prop="name" label="设备ID"></el-table-column>

                <el-table-column prop="name" label="设备名称"></el-table-column>
                <el-table-column prop="name" label="设备种类"></el-table-column>
                <el-table-column prop="name" label="型号描述"></el-table-column>
                <el-table-column prop="name" label="出厂编号"></el-table-column>
                <el-table-column prop="name" label="客户名称"></el-table-column>

                <el-table-column prop="name" label="主机温度(℃)"></el-table-column>
                <el-table-column prop="name" label="水箱温度(℃)"></el-table-column>
                <el-table-column prop="name" label="进口温度(℃)"></el-table-column>
                <el-table-column prop="name" label="出口温度(℃)"></el-table-column>
                <el-table-column prop="name" label="压力"></el-table-column>
                <el-table-column prop="name" label="压差"></el-table-column>
                <el-table-column prop="name" label="电机转速(转/分)"></el-table-column>
                <el-table-column prop="name" label="电流(A)"></el-table-column>
                <el-table-column prop="name" label="主油箱液位(mm)"></el-table-column>
                <el-table-column prop="name" label="主油箱温度(℃)"></el-table-column>
                <el-table-column prop="name" label="供油管路温度(℃)"></el-table-column>
                <el-table-column prop="name" label="紧急过滤器压差"></el-table-column>
                <el-table-column prop="name" label="双筒过滤器压差"></el-table-column>
                <el-table-column prop="name" label="高位油箱液位(mm)"></el-table-column>
                <el-table-column prop="name" label="控制油压力"></el-table-column>
                <el-table-column prop="name" label="润滑油出口压力"></el-table-column>
                <el-table-column prop="name" label="电机泵组震动"></el-table-column>
                <el-table-column prop="name" label="电机电流"></el-table-column>
                <el-table-column prop="name" label="主油箱油品分析"></el-table-column>
                <el-table-column prop="name" label="故障代码"></el-table-column>
                <el-table-column prop="name" label="运行时长(h)"></el-table-column>
                <el-table-column prop="name" label="工作状态"></el-table-column>
                <el-table-column prop="name" label="开关机"></el-table-column>
                <el-table-column prop="name" label="更新日期"></el-table-column>

                <el-table-column label="操作" width="180" align="center">
                    <template slot-scope="scope">
                        <el-button
                            type="text"
                            icon="el-icon-edit"
                            @click="handleEdit(scope.$index, scope.row)"
                        >编辑</el-button>
                        <el-button
                            type="text"
                            icon="el-icon-delete"
                            class="red"
                            @click="handleDelete(scope.$index, scope.row)"
                        >删除</el-button>
                    </template>
                </el-table-column>
            </el-table>
            <div class="pagination">
                <el-pagination
                    background
                    layout="total, prev, pager, next"
                    :current-page="query.pageIndex"
                    :page-size="query.pageSize"
                    :total="pageTotal"
                    @current-change="handlePageChange"
                ></el-pagination>
            </div>
        </div>

        <!-- 编辑弹出框 -->
        <el-dialog title="编辑" :visible.sync="editVisible" width="30%">
            <el-form ref="form" :model="form" label-width="70px">
                <el-form-item label="用户名">
                    <el-input v-model="form.name"></el-input>
                </el-form-item>
                <el-form-item label="地址">
                    <el-input v-model="form.address"></el-input>
                </el-form-item>
            </el-form>
            <span slot="footer" class="dialog-footer">
                <el-button @click="editVisible = false">取 消</el-button>
                <el-button type="primary" @click="saveEdit">确 定</el-button>
            </span>
        </el-dialog>
    </div>
</template>

<script>
import { fetchData } from '../../api/index';
export default {
    name: 'basetable',
    data() {
        return {
            visible: false,
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
            },
            value1: '',
            value2: '',
            query: {
                address: '',
                name: '',
                pageIndex: 1,
                pageSize: 10
            },
            tableData: [],
            multipleSelection: [],
            delList: [],
            editVisible: false,
            pageTotal: 0,
            form: {},
            idx: -1,
            id: -1
        };
    },
    created() {
        this.getData();
    },
    methods: {
        // 获取 easy-mock 的模拟数据
        getData() {
            fetchData(this.query).then(res => {
                console.log(res);
                this.tableData = res.list;
                this.pageTotal = res.pageTotal || 50;
            });
        },
        // 触发搜索按钮
        handleSearch() {
            this.$set(this.query, 'pageIndex', 1);
            this.getData();
        },
        // 删除操作
        handleDelete(index, row) {
            // 二次确认删除
            this.$confirm('确定要删除吗？', '提示', {
                type: 'warning'
            })
                .then(() => {
                    this.$message.success('删除成功');
                    this.tableData.splice(index, 1);
                })
                .catch(() => {});
        },
        // 多选操作
        handleSelectionChange(val) {
            this.multipleSelection = val;
        },
        delAllSelection() {
            const length = this.multipleSelection.length;
            let str = '';
            this.delList = this.delList.concat(this.multipleSelection);
            for (let i = 0; i < length; i++) {
                str += this.multipleSelection[i].name + ' ';
            }
            this.$message.error(`删除了${str}`);
            this.multipleSelection = [];
        },
        // 编辑操作
        handleEdit(index, row) {
            this.idx = index;
            this.form = row;
            this.editVisible = true;
        },
        // 保存编辑
        saveEdit() {
            this.editVisible = false;
            this.$message.success(`修改第 ${this.idx + 1} 行成功`);
            this.$set(this.tableData, this.idx, this.form);
        },
        // 分页导航
        handlePageChange(val) {
            this.$set(this.query, 'pageIndex', val);
            this.getData();
        }
    }
};
</script>

<style scoped>
.handle-box {
    margin-bottom: 20px;
}

.handle-select {
    width: 120px;
}

.handle-input {
    width: 300px;
    display: inline-block;
}
.table {
    width: 100%;
    font-size: 14px;
}
.red {
    color: #ff0000;
}
.mr10 {
    margin-right: 10px;
}
.table-td-thumb {
    display: block;
    margin: auto;
    width: 40px;
    height: 40px;
}
.product-status {
    margin-bottom: 10px;
    display: flex;
    justify-content: space-between;
}
.mt-10 {
    margin-bottom: 10px;
}
th {
    background-color: #eef1f6;
    padding: 5px 15px;
}
td {
    padding: 5px 15px;
}
table {
    margin: 0 auto;
    width: 90%;
    border: 1px solid #cdcdcd;
    text-align: center;
}
</style>

