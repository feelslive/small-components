<template>
  <div class="warn">
    <div class="m-alert" :class="[classes]" :style="styles">
      <slot name="icon">
        <i v-if="showicon" class="m-icon">#</i>
      </slot>
      <div class="m-content">
        <slot name="title">
          <span class="m-meg">{{title}}</span>
        </slot>
        <i v-if="closes" class="m-closebtn" @click="close">X</i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'warn',
  props:{
    type:{
      type:String,
      default:"info"
    },
    title:{
      type:String,
      default:"这有一个提示消息"
    },
    closes:{
      type:Boolean,
      default:true
    },
    showicon:{
      type:Boolean,
      default:true
    },
    styles:{
      type:String,
      default:''
    }
  },
  computed:{
      classes(){
        return `m-alert-${this.type}`
      }
  },
  methods:{
      close(){
        this.$emit("close")
      }
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.warn{
  width: 500px;
  margin: 0 auto;
}
.m-alert{
  width: 100%;
  padding: 8px 16px;
  margin: 0 auto;
  box-sizing: border-box;
  border-radius: 4px;
  position: relative;
  background-color: #fff;
  overflow: hidden;
  color: #fff;
  display: table;
  transform:opacity .2s;
  margin-top: 10px;
  border: 1px solid #ccc;
}
.m-content{
  display: table-cell;
  padding: 0 8px;
}
.m-meg {
  font-size: 13px;
  line-height: 18px;
}
.m-alert-success{
  background-color: #13ce66;
}
.m-alert-info{
  background-color: #50bfff;
}
.m-alert-warning{
  background-color: #f7ba22;
}
.m-alert-error{
  background-color: #ff4949;
}
.m-closebtn{
  font-size: 12px;
  color: #fff;
  opacity:1;
  top: 12px;
  right:15px;
  position: absolute;
  cursor:pointer;
}
.m-icon{
  font-size: 16px;
  width: 16px;
  display: table-cell;
  color: #fff;
  vertical-align: middle;
}
</style>
