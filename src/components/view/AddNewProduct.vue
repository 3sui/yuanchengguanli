<!--
 * @Author: your name
 * @Date: 2020-05-06 14:19:13
 * @LastEditTime: 2020-05-06 14:43:51
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \vue-manage-system\src\components\view\AddNewProduct.vue
 -->
<template>
    <div>
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item>
                    <i class="el-icon-lx-calendar"></i> 产品档案
                </el-breadcrumb-item>
                <el-breadcrumb-item>添加产品</el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="container">
            <div class="form-box">
                <el-form ref="form" :model="form" label-width="120px">
                    <el-form-item label="设备ID">
                        <el-input v-model="form.name"></el-input>
                    </el-form-item>
                    <el-form-item label="设备种类">
                        <el-select v-model="form.region" placeholder="请选择">
                            <el-option key="bbk" label="干燥设备" value="bbk"></el-option>
                            <el-option key="xtc" label="液压设备" value="xtc"></el-option>
                        </el-select>
                    </el-form-item>
                    <el-form-item label="设备名称">
                        <el-input v-model="form.name"></el-input>
                    </el-form-item>
                    <el-form-item label="型号描述">
                        <el-input v-model="form.name"></el-input>
                    </el-form-item>
                    <el-form-item label="出厂编号">
                        <el-input v-model="form.name"></el-input>
                    </el-form-item>
                    <el-form-item label="所属客户名称">
                        <el-input v-model="form.name"></el-input>
                    </el-form-item>
                    <el-form-item label="客户行业">
                        <el-input v-model="form.name"></el-input>
                    </el-form-item>
                    <el-form-item label="安装地址">
                        <el-cascader
                            size="large"
                            :options="options"
                            v-model="selectedOptions"
                            @change="handleChange"
                        ></el-cascader>
                    </el-form-item>
                    <el-form-item label="详细地址">
                        <el-input v-model="form.name"></el-input>
                    </el-form-item>

                    <el-form-item>
                        <el-button type="primary" @click="onSubmit">提交</el-button>
                        <el-button>取消</el-button>
                    </el-form-item>
                </el-form>
            </div>
        </div>
    </div>
</template>

<script>
import { provinceAndCityData, regionData, provinceAndCityDataPlus, regionDataPlus, CodeToText, TextToCode } from 'element-china-area-data';
export default {
    name: 'baseform',
    data() {
        return {
            options: provinceAndCityData,
            form: {
                name: '',
                region: '',
                date1: '',
                date2: '',
                delivery: true,
                type: ['步步高'],
                resource: '小天才',
                desc: '',
                options: []
            }
        };
    },
    methods: {
        onSubmit() {
            this.$message.success('提交成功！');
        }
    }
};
</script>
<style scoped>
.form-box {
    margin: 0 auto;
}
</style>