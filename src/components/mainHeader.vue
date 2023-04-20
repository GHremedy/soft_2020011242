<template>
    <div class="toolbar" v-if="isLogged" >
        <el-dropdown>
            <el-icon style="margin-right: 8px; margin-top: 1px">
                <Setting />
            </el-icon>
            <template #dropdown>
                <el-dropdown-menu>
                    <el-dropdown-item>View</el-dropdown-item>
                    <el-dropdown-item>Add</el-dropdown-item>
                    <el-dropdown-item>Delete</el-dropdown-item>
                </el-dropdown-menu>
            </template>
        </el-dropdown>
        <span>Tom</span>
    </div>
    <div class="toolbar" v-if="!isLogged">
        <signUp/>
        <logIn/>
    </div>
</template>

<script>

import { Setting } from '@element-plus/icons-vue';
import { provide } from 'vue';
import signUp from './signUp.vue';
import logIn from './logIn.vue';
export default {
    name: 'mainHeader',
    setup() {
        let isLogged = false
        provide('isLogged',isLogged)
        return {isLogged}
    },
    components:{
        Setting,
        signUp,
        logIn
    }
}
</script>

<style>
.el-header {
    position: relative;
    background-color: var(--el-color-primary-light-7);
    color: var(--el-text-color-primary);
}

.toolbar {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    height: 100%;
    right: 20px;
}
</style>