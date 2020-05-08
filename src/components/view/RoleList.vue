<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-lx-cascades"></i> 角色设置
                </el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="container">
            <div class="handle-box">
                <el-button type="primary" class="handle-del mr10" @click="delAllSelection" icon="el-icon-plus">新增</el-button>

                <el-input v-model="query.name" placeholder="名称" class="handle-input mr10"></el-input>
                <el-button type="primary" icon="el-icon-search" @click="handleSearch">搜索</el-button>
                <div class="block datechoose">
                    <span class="demonstration">创建日期</span>
                    &nbsp;
                    <el-date-picker
                        v-model="value1"
                        type="daterange"
                        range-separator="至"
                        start-placeholder="开始日期"
                        end-placeholder="结束日期"
                    ></el-date-picker>
                </div>
            </div>

            <!-- 表格列 -->
            <el-table
                :data="tableData"
                border
                class="table"
                ref="multipleTable"
                header-cell-class-name="table-header"
                @selection-change="handleSelectionChange"
            >
                <!-- 复选框 -->
                <el-table-column type="selection" width="55" align="center"></el-table-column>
                <!-- 序号 -->
                <el-table-column prop="id" label="序号" width="55" align="center"></el-table-column>
                <!-- 角色 -->
                <el-table-column prop="role" label="角色" align="center"></el-table-column>
                <!-- 角色描述 -->
                <el-table-column prop="roleDescription" label="角色描述" align="center"></el-table-column>
                <!-- 用户 -->
                <el-table-column prop="userList" label="用户" align="center"></el-table-column>
                <!-- 用户数 -->
                <el-table-column prop="userSum" label="用户数" align="center"></el-table-column>
                <!-- 创建时间 -->
                <el-table-column prop="createtime" label="创建时间" align="center"></el-table-column>
                <!-- 操作 -->
                <el-table-column label="操作" width="180" align="center">
                    <template slot-scope="scope">
                        <el-button
                            type="text"
                            icon="el-icon-edit"
                            @click="handleEdit(scope.$index, scope.row)"
                        >编辑</el-button>
                        <el-button
                            type="text"
                            icon="el-icon-view"
                            @click="handleEdit(scope.$index, scope.row)"
                        >查看</el-button>
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
        <el-dialog title="新增/编辑" :visible.sync="editVisible" width="30%">
            <el-form ref="form" :model="form" label-width="70px">
                <el-form-item label="角色名">
                    <el-input v-model="form.address"></el-input>
                </el-form-item>
                <el-form-item label="角色描述">
                    <el-input v-model="form.address"></el-input>
                </el-form-item>
                <el-divider>功能权限</el-divider>
                <label>请选择角色可使用功能</label>
                <el-tree
                    :data="data"
                    show-checkbox
                    node-key="id"
                    :default-expanded-keys="[2, 3]"
                    :default-checked-keys="[5]"
                    :props="defaultProps"
                ></el-tree>
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
    name: 'RoleList',
    data() {
        return {
            data: [
                {
                    id: 1,
                    label: 'PC',
                    children: [
                        {
                            id: 2,
                            label: '用户地图',
                            children: [
                                {
                                    id: 8,
                                    label: '查询'
                                },
                                {
                                    id: 9,
                                    label: '导出'
                                }
                            ]
                        },
                        {
                            id: 2,
                            label: '产品档案',
                        },
                        {
                            id: 3,
                            label: '远程监控',
                        },
                        {
                            id: 4,
                            label: '服务手册',
                        },
                        {
                            id: 5,
                            label: '报警记录',
                        },
                        {
                            id: 6,
                            label: '交易分析',
                        },
                        {
                            id: 7,
                            label: '基础数据管理',
                            children: [
                                {
                                    id: 10,
                                    label: '数据字典'
                                },
                                {
                                    id: 11,
                                    label: '用户管理'
                                },
                                {
                                    id: 12,
                                    label: '角色管理'
                                },
                                {
                                    id: 13,
                                    label: '报警设置'
                                }
                            ]
                        }
                    ]
                } 
            ],
            defaultProps: {
                children: 'children',
                label: 'label'
            },
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
.datechoose {
    float: right;
}
</style>
