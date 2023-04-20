<template>
    <div>
        <el-button text @click="logInFormVisible = true" style="color: black;">
            登录
        </el-button>
        <el-dialog v-model="logInFormVisible" title="">
            <el-form :model="logInForm">
                <el-form-item label="用户名" :label-width="formLabelWidth">
                    <el-input v-model="logInForm.username" placeholder="请输入你的用户名" />
                </el-form-item>
                <el-form-item label="密码" :label-width="formLabelWidth">
                    <el-input type="password" v-model="logInForm.password" placeholder="请输入你的密码" />
                </el-form-item>
            </el-form>
            <template #footer>
                <span>
                    <el-button @click="logInFormVisible = false">取消</el-button>
                    <el-button type="primary" @click="logIn()">确定</el-button>
                </span>
            </template>
        </el-dialog>
    </div>
</template>

<script>
import { ref, reactive ,inject} from 'vue';
import axios from 'axios';
export default {
    setup() {
        let logInFormVisible = ref(false)

        let isFormValid = ref(false)

        const formLabelWidth = '140px'

        let logInForm = reactive({
            name: '',
            password: ''
        })
        let isLogged = inject('isLogged')
        function logIn(logInForm) {
            if (isFormValid) {
                axios.get('/login', logInForm).then(res => {
                    logInFormVisible = false
                    isLogged = true
                    alert('登录成功')
                })
            }
            else{
                alert('请完整输入登录项')
            }
        }

        return {formLabelWidth,isFormValid,isLogged,logInForm,logIn,logInFormVisible}
    }
}
</script>

<style lang="scss" scoped></style>