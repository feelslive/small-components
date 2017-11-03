<template>
  <div id="app">

    <h2>提示条组件</h2>
    <!-- 提示条组件 -->
    <warn type="success" title="默认" @close="close"></warn>
    <warn type="error" title="默认"></warn>
    <warn type="warning" title="控制按钮" :closes="false"></warn>
    <warn type="info" title="控制图标" :showicon="false"></warn>
    <warn type="success" title="定制颜色" styles="background-color:pink;"></warn>
     <warn type="success">
       <p slot="title">定制消息</p>
     </warn>
      <warn type="success" title="定制图标">
        <i slot="icon">$</i>
     </warn>


    <h2>模态框组件</h2>
     <!-- 模态框组件 -->
    <modal modal-title="提醒" @cancel="cancel" @confirm="confirm"></modal>
    <modal modal-title="自定义内容和按钮">
        <ul slot="modal-content">
          <li v-for="item in list">{{item}}</li>
        </ul>
        <div slot="modal-foot">
          <span>确定</span>
          <span>取消</span>
          <span>返回</span>
        </div>
    </modal>


    <h2>树形菜单组组件</h2>
    <!-- 树形菜单组组件 -->
    <treemenu :tree="tree"></treemenu>


    
    <h2>动态切换组件</h2>
    <!-- 动态切换组件 -->
    <div class="div">
      <input type="button" value="第一个组件" @click="tab(1)"/>
      <input type="button" value="第二个组件" @click="tab(2)"/>
      <input type="button" value="第三个组件" @click="tab(3)"/>
      <!-- keep保留组件状态 -->
      <keep-alive>
        <component :is="current"></component>
      </keep-alive>
    </div>
    
    <router-view/>
  </div>
</template>

<script>
import warn from "./components/warn.vue"
import modal from "./components/modal.vue"
import treemenu from "./components/treemenu.vue"
import dt1 from "./components/dtcoms/dt1.vue"
import dt2 from "./components/dtcoms/dt2.vue"
import dt3 from "./components/dtcoms/dt3.vue"
export default {
  name: 'app',
  data(){
    return{
        list:["A","B","C"],
        tree:[{
          title:"目录",
          chindren:[{
            title:"我的音乐",
            chindren:[{
              title:"刘德华",
              chindren:[{
                title:"爱你一万年"
              },
              {
                title:"忘情水"
              }]
            },{
              title:"张学友",
              chindren:[{
                title:"吻别"
              },{
                title:"饿狼传说"
              }]
            }]
          },{
            title:"我的照片"
          }]
        }],
        current:dt1
    }
  },
  methods:{
    cancel(){
      alert("取消了")
    },
    confirm(){
      alert("确定了")
    },
    close(){
      alert("关闭提醒")
    },
    tab(index){
      if(index===1){
        this.current = dt1
      }else if(index===2){
        this.current = dt2
      }else if(index===3){
        this.current = dt3
      }
    }
  },
  components:{
    warn,
    modal,
    treemenu,
    dt1,
    dt2,
    dt3
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  overflow: hidden;
}
h2{
  margin: 20px 0;
  font-weight: bold;
}
.div {
  height: 200px;
  width: 300px;
  margin: 20px auto;
  border: 1px solid #000;
}
</style>
