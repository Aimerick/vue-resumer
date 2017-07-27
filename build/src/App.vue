<template>
  <div id="app" v-bind:class="{previewMode: previewMode}">
    <Topbar class="topbar" v-on:preview="preview"/>
    <main>
      <Editor v-bind:resume="resume" class="editor"/>
      <Preview v-bind:resume="resume" class="preview"/>
    </main>
    <el-button id="exitPreview" v-on:click="exitPreview">退出预览</el-button>
  </div>
</template>

<script>
import Editor from './components/Editor'
import Topbar from './components/Topbar'
import Preview from './components/Preview'

export default {
  name: 'app',
  data(){
    return{
      previewMode: false,
      resume: {
          profile: {
              name: '',
              city: '',
              birth: ''
          },
          workHistory: [
              {company:'', time:'', content:''},
          ],
          studyHistory: [
              {school:'', duration:'', degree:''},
          ],
          projects: [
              {name:'', content:''},
          ],
          awards: [
              {name: ''},
          ],
          contacts: {
              phone:'', email:'', QQ:'', wechat:''
          },
      }
    }
  },
  components: {
    Topbar, Editor, Preview
  },
  methods: {
    preview(){
      this.previewMode = true
    },
    exitPreview(){
      this.previewMode = false
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.icon {
  width: 1em; height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}

.topbar{
  box-shadow: 0 0 3px hsla(0,0,0,0.5);
  position: relative;
  z-index: 1;
}

main{
  background: #ddd;
  display: flex;
  flex:1;
  > .editor{
    width: 40em;
    margin: 16px 8px 16px 16px;
    background: #fff;
    box-shadow: 0 0 3px hsla(0,0,0,0.5);
    border-radius: 4px;
    overflow: auto;
  }

  > .preview{
    flex: 1;
    margin: 16px 16px 16px 8px;
    background: #fff;
    box-shadow: 0 0 3px hsla(0,0,0,0.5);
    boeder-radius: 4px;
    overflow: hidden;
  }
}

.previewMode > #topbar{
  display: none;
}

.previewMode #editor{
  display: none;
}

.previewMode #preview{
  max-width: 800px;
  margin: 32px auto;
}

#exitPreview{
  display: none;
}

.previewMode #exitPreview{
  display: inline-block;
  position: fixed;
  right: 16px;
  bottom: 16px;
}

</style>


