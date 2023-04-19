<template>
    <div>
        <el-container style="height: 500px">
            <el-aside width="200px">
                <mainAside />
            </el-aside>
            <el-container>
                <el-header style="text-align: right; font-size: 12px">
                    <mainHeader />
                </el-header>
                <el-main>
                    <mainContainer />
                </el-main>
            </el-container>
        </el-container>
    </div>
</template>

<script lang="ts" setup>

import mainAside from './components/mainAside.vue';
import mainContainer from './components/mainContainer.vue';
import mainHeader from './components/mainHeader.vue';



</script>

<style scoped></style>
