<!--
 * @Author: your name
 * @Date: 2020-05-07 14:21:47
 * @LastEditTime: 2020-05-07 14:33:45
 * @LastEditors: Please set LastEditors
 * @Description: 服务手册
 * @FilePath: \vue-manage-system\src\components\view\ServiceBooklet.vue
 -->
<!--  -->
<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-lx-cascades"></i> 服务手册
                </el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="container">
            <el-button type="primary" icon="el-icon-delete" class="handle-del mr10 mb-30">添加</el-button>
            <el-button type="primary" icon="el-icon-delete" class="handle-del mr10 mb-30">导入</el-button>
            <el-collapse v-model="activeName" accordion>
                <el-collapse-item title="振动噪音大" name="1">
                    <table>
                        <thead>
                            <tr>
                                <th>可能产生的原因</th>
                                <th>排除办法</th>
                                <th>操作</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>吸入管路或泵吸入端漏气、堵塞</td>
                                <td>消除漏气、堵塞</td>
                                <td>
                                    <a href="javascript: void(0)">编辑</a> /
                                    <a href="javascript: void(0)">删除</a>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </el-collapse-item>
                <el-collapse-item title="振动噪音大" name="2">
                    <table>
                        <thead>
                            <tr>
                                <th>可能产生的原因</th>
                                <th>排除办法</th>
                                <th>操作</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>吸入管路或泵吸入端漏气、堵塞</td>
                                <td>消除漏气、堵塞</td>
                                <td>
                                    <a href="javascript: void(0)">编辑</a> /
                                    <a href="javascript: void(0)">删除</a>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </el-collapse-item>
                <el-collapse-item title="振动噪音大" name="3">
                    <table>
                        <thead>
                            <tr>
                                <th>可能产生的原因</th>
                                <th>排除办法</th>
                                <th>操作</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>吸入管路或泵吸入端漏气、堵塞</td>
                                <td>消除漏气、堵塞</td>
                                <td>
                                    <a href="javascript: void(0)">编辑</a> /
                                    <a href="javascript: void(0)">删除</a>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </el-collapse-item>
                <el-collapse-item title="振动噪音大" name="4">
                    <table>
                        <thead>
                            <tr>
                                <th>可能产生的原因</th>
                                <th>排除办法</th>
                                <th>操作</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>吸入管路或泵吸入端漏气、堵塞</td>
                                <td>消除漏气、堵塞</td>
                                <td>
                                    <a href="javascript: void(0)">编辑</a> /
                                    <a href="javascript: void(0)">删除</a>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </el-collapse-item>
                <el-collapse-item title="振动噪音大" name="5">
                    <table>
                        <thead>
                            <tr>
                                <th>可能产生的原因</th>
                                <th>排除办法</th>
                                <th>操作</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>吸入管路或泵吸入端漏气、堵塞</td>
                                <td>消除漏气、堵塞</td>
                                <td>
                                    <a href="javascript: void(0)">编辑</a> /
                                    <a href="javascript: void(0)">删除</a>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </el-collapse-item>
                <el-collapse-item title="振动噪音大" name="6">
                    <table>
                        <thead>
                            <tr>
                                <th>可能产生的原因</th>
                                <th>排除办法</th>
                                <th>操作</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>吸入管路或泵吸入端漏气、堵塞</td>
                                <td>消除漏气、堵塞</td>
                                <td>
                                    <a href="javascript: void(0)">编辑</a> /
                                    <a href="javascript: void(0)">删除</a>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </el-collapse-item>
            </el-collapse>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ServiceBooklet',
    data() {
        return {
            activeName: '1'
        };
    },

    components: {},

    computed: {},

    methods: {}
};
</script>
<style scoped>
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
    /* border: 1px solid #cdcdcd; */
    text-align: center;
}
.mb-30 {
    margin-bottom: 30px;
}
</style>