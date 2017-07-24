<template>
    <div>
        <h2>学习经历</h2>
            <el-form>
                <div v-for="(work, index) in studyHistory" class="container">
                    <el-form-item label="学校">
                        <el-input v-model="studyHistory.school"></el-input>
                    </el-form-item>
                    <el-form-item label="时间">
                        <el-input v-model="studyHistory.time"></el-input>
                    </el-form-item>
                    <el-form-item label="学位">
                        <el-input v-model="studyHistory.degree"></el-input>
                    </el-form-item>
                    <i class="el-icon-close" v-on:click="removestudyHistory(index)"></i> 
                    <hr>                                   
                </div>
                <el-button :plain="true" type="info" v-on:click="addstudyHistory">添加</el-button>
            </el-form>
    </div>
</template>

<script>
    export default{
        props: ['studyHistory'],
        methods: {
            addstudyHistory(){
                this.studyHistory.push({
                    school:'', time:'', degree:''
                })
            },
            removestudyHistory(index){
                this.studyHistory.splice(index, 1)
            }
        }
    }
</script>