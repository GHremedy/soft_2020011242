<template>
    <div>
        <el-button text @click="signUpFormVisible = true">
        </el-button>

        <el-dialog v-model="signUpFormVisible" title="注册">
            <el-form :model="signUpForm">
                <el-form-item label="姓名" :label-width="formLabelWidth">
                    <el-input v-model="signUpForm.name" autocomplete="off" placeholder="请输入你的名字" />
                </el-form-item>
                <el-form-item label="用户名" :label-width="formLabelWidth">
                    <el-input v-model="signUpForm.username" placeholder="请输入你的用户名" />
                </el-form-item>
                <el-form-item label="密码" :label-width="formLabelWidth">
                    <el-input v-model="signUpForm.password" placeholder="请输入你的密码" />
                </el-form-item>

            </el-form>
            <template #footer>
                <span class="dialog-footer">
                    <el-button @click="signUpFormVisible = false">Cancel</el-button>
                    <el-button type="primary" @click="signUpFormVisible = false">
                        Confirm
                    </el-button>
                </span>
            </template>
        </el-dialog>
    </div>
</template>

<script>

import { reactive, ref } from 'vue'
export default {
    setup() {

        const signUpFormVisible = ref(false)
        const formLabelWidth = '140px'

        const signUpForm = reactive({
            name: '',
            username: '',
            password: '',
            email: '',
            phoneNumber: '',
            sex: '',
            city: '',
            bankCardNumber: '',
        })

        const city = reactive([
            {
                name: '北京',
                label: 'beijing'
            },
            {
                name: '天津',
                label: 'tianjing'
            },
            {
                name: '山东',
                label: 'shandong'
            },
            {
                name: '河北',
                label: 'hebei'
            },
            {
                name: '河南',
                label: 'henan'
            }
        ])

        return {signUpFormVisible,signUpForm,city,formLabelWidth}
    }
}
</script>

<style ></style>