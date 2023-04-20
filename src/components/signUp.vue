<template>
    <div>
        <el-button text @click="signUpFormVisible = true" style="color: black;">
            注册
        </el-button>
        <el-dialog v-model="signUpFormVisible" title="">
            <el-form :model="signUpForm">
                <el-form-item label="姓名" :label-width="formLabelWidth">
                    <el-input v-model="signUpForm.name" autocomplete="off" placeholder="请输入你的名字" />
                </el-form-item>
                <el-form-item label="用户名" :label-width="formLabelWidth">
                    <el-input v-model="signUpForm.username" placeholder="请输入你的用户名" />
                </el-form-item>
                <el-form-item label="密码" :label-width="formLabelWidth">
                    <el-input type="password" v-model="signUpForm.password" placeholder="请输入你的密码" />
                </el-form-item>
                <el-form-item label="邮箱" :label-width="formLabelWidth">
                    <el-input v-model="signUpForm.email" placeholder="请输入你的邮箱" />
                </el-form-item>
                <el-form-item label="电话号码" :label-width="formLabelWidth">
                    <el-input v-model="signUpForm.phoneNumber" placeholder="请输入你的电话号码" />
                </el-form-item>
                <el-form-item label="性别" :label-width="formLabelWidth">
                    <el-radio-group v-model="signUpForm.sex">
                        <el-radio label="男">男</el-radio>
                        <el-radio label="女">女</el-radio>
                    </el-radio-group>
                </el-form-item>
                <el-form-item label="城市" :label-width="formLabelWidth">
                    <el-select v-model="signUpForm.city" placeholder="请选择你的城市">
                        <el-option v-for="city in cities" :key="city.name" :label="city.name"
                            :value="city.name"></el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="银行卡号" :label-width="formLabelWidth">
                    <el-input v-model="signUpForm.bankCardNumber" placeholder="请输入你的银行卡号"></el-input>
                </el-form-item>
            </el-form>
            <template #footer>
                <span>
                    <el-button @click="signUpFormVisible = false">取消</el-button>
                    <el-button type="primary" @click="signUp()">确定</el-button>
                </span>
            </template>
        </el-dialog>
    </div>
</template>

<script>

import { reactive, ref } from 'vue'
import axios from 'axios'
export default {
    setup() {

        let signUpFormVisible = ref(false)

        let isFormValid = ref(false)

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

        const cities = [
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
        ]

        function signUp(signUpForm) {
            if (isFormValid) {
                axios.post('/signup', signUpForm).then(res => {
                    signUpFormVisible = false
                    alert('注册成功')
                })
            }
            else {
                alert('请完整输入注册项')
            }
        };

        computed: {
            function isFormCompleted(){
                    isFormValid = signUpForm.name !== '' && signUpForm.username !== '' && signUpForm.password !== ''
                        && signUpForm.email !== '' && signUpForm.phoneNumber !== '' && signUpForm.sex !== '' &&
                        signUpForm.city !== '' && signUpForm.bankCardNumber !== ''
                    return isFormValid
            }
        }



        return { signUpFormVisible, signUpForm, cities, formLabelWidth, signUp, isFormValid }
    }
}
</script>

<style ></style>