<template>
    <div>
        <h2>工作经历</h2>
            <el-form>
                <div v-for="(work, index) in workHistory" class="container">
                    <el-form-item label="公司">
                        <el-input v-model="workHistory.company"></el-input>
                    </el-form-item>
                    <el-form-item label="工作年份">
                        <el-input v-model="workHistory.time"></el-input>
                    </el-form-item>
                    <el-form-item label="工作内容">
                        <el-input v-model="workHistory.content"></el-input>
                    </el-form-item>
                    <i class="el-icon-close" v-on:click="removeWorkHistory(index)"></i> 
                    <hr>                                   
                </div>
                <el-button :plain="true" type="info" v-on:click="addWorkHistory">添加</el-button>
            </el-form>
    </div>
</template>

<script>
    export default{
        props: ['workHistory'],
        methods: {
            addWorkHistory(){
                this.workHistory.push({
                    company:'', time:'', content:''
                })
            },
            removeWorkHistory(index){
                this.workHistory.splice(index, 1)
            }
        }
    }
</script>