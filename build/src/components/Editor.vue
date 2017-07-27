<template>
<div id="editor">
    <nav>
        <ol>
            <li v-for="i in [0,1,2,3,4,5]" 
                v-bind:class="{active:currentTab===i}" 
                v-on:click = "currentTab = i"
                >
                <svg class="icon">
                    <use v-bind:xlink:href="`#${icons[i]}`"></use>
                </svg>
            </li>        
        </ol>
    </nav>
    <ol className="panes">
        <li v-bind:class="{active:currentTab===0}">
           <ProfileEditor v-bind:profile="resume.profile"/>
        </li>
        <li v-bind:class="{active:currentTab===1}">
            <ItemsEditor v-bind:items="resume.workHistory" v-bind:labels="{company:'公司', time:'时间', content:'工作内容'}" title="工作经历"/>
        </li>
        <li v-bind:class="{active:currentTab===2}">
            <ItemsEditor v-bind:items="resume.studyHistory" v-bind:labels="{school:'学校', duration:'时间', degree:'学位'}" title="学习经历"/>
        </li>
        <li v-bind:class="{active:currentTab===3}">
            <ItemsEditor v-bind:items="resume.projects" v-bind:labels="{name:'项目名称', content:'项目内容'}" title="项目经历"/>
        </li>
        <li v-bind:class="{active:currentTab===4}">
            <ItemsEditor v-bind:items="resume.awards" v-bind:labels="{name:'奖励详情'}" title="获奖情况"/>
        </li>
        <li v-bind:class="{active:currentTab===5}">
            <h2>联系方式</h2>
            <el-form v-bind:submit="onSubmit">
                <el-form-item label="手机号码">
                    <el-input v-model="resume.contacts.phone"></el-input>
                </el-form-item>
                <el-form-item label="邮箱">
                    <el-input v-model="resume.contacts.email"></el-input>
                </el-form-item>
                <el-form-item label="QQ">
                    <el-input v-model="resume.contacts.email"></el-input>
                </el-form-item>
                <el-form-item label="微信 *">
                    <el-input v-model="resume.contacts.wechat"></el-input>
                </el-form-item>
            </el-form>
        </li>
    </ol>
</div>
</template>

<script>
    import ProfileEditor from './ProfileEditor'
    import ItemsEditor from './ItemsEditor'
    export default{
        onSubmit: 'app',
        components:{ ProfileEditor , ItemsEditor},
        props: ['resume'],
        data(){
            return{
                onSubmit: '',
                currentTab: 0,
                icons: ['icon-shenfenzheng', 'icon-gongzuojingyan', 'icon-study', 'icon-heart',  'icon-jiangbei-copy', 'icon-phone'],
            }
        },

        methods: {
            
        }

    }
</script>

<style lang="scss">
    #editor{
        display: flex;
        min-height: 100px;
        > nav{
            background: #000;
            width: 80px;
            height: 100%;
        }
        min-height: 100px;
        nav > ol > li {
            padding: 8px 0;
            text-align: center;
            > .icon{
                width: 24px;
                height: 24px;
                fill: #fff;
            }
            &.active{
                background: #fff;
                
                > .icon{
                    fill: black;
                }
            }
        }

        > ol 
        {
            .container{
                position: relative;
                margin-bottom: 16px;
                .el-icon-close{
                    position: absolute;
                    right: 0;
                    top: 0;
                    font-size: 8px;
                }
            }
            flex: 1;
            > li{
                display: none;
                padding: 32px;
                height: 100%;
                overflow: auto;
                &.active{
                    display: block;
                }
            }
        }
    }

    
</style>

