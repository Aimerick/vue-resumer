<template>
    <div id="topbar">
        <div class="logo">VueResumer</div>
        <div class="actions">
            <el-button v-on:click="preview">预览</el-button>
            <el-button>登陆</el-button>
            <el-button type="primary">注册</el-button>
        </div>
    </div>
</template>

<style lang="scss">
    #topbar{
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 24px;
        font-size: 20px;
    }
</style>

<script>
    export default{
        methods:{
            preview(){
                this.$emit('preview')
            }
        }
    }
</script>