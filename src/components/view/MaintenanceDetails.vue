<!--
 * @Author: your name
 * @Date: 2020-05-06 10:56:10
 * @LastEditTime: 2020-05-06 15:36:08
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \vue-manage-system\src\components\view\ProductDetails.vue
 -->
<!--  -->
<template>
    <div class>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-lx-copy"></i> 维修记录
                </el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="container">
            <el-button type="primary" icon="el-icon-delete" class="handle-del mr10 mb-30">返回</el-button>
            <div class="plugins-tips">设备信息</div>
            <el-row :gutter="20" class="mb-30">
                <el-col :span="12">
                    <div class="ml-50">
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                        <p>设备ID:{{}}</p>
                    </div>
                </el-col>
                <el-col :span="12">
                    <div class="ml-50">
                        <img
                            width="100%"
                            src="http://127.0.0.1:5500/images/%E4%BA%A7%E5%93%81%E8%AF%A6%E6%83%85/u711.png"
                            alt
                        />
                    </div>
                </el-col>
            </el-row>
            <div class="plugins-tips">维修记录</div>
            <div class="ml-50">
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
                <p>设备ID:{{}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'productDetails',
    data() {
        return {};
    },

    components: {},

    computed: {},

    methods: {}
};
</script>
<style scoped>
th {
    background-color: #eef1f6;
    padding: 5px 10px;
}
td {
    padding: 5px 10px;
}
p {
    line-height: 25px;
}
.ml-50 {
    margin-left: 50px;
}
.mb-30 {
    margin-bottom: 30px;
}
.mt-10 {
    margin-top: 10px;
}
.annex img {
    margin: 10px 10px;
    vertical-align: middle;
}
</style>