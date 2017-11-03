<template>
	<div class="tree-menu-comm tree-menu">
		<treelist :trees="tree"></treelist>
	</div>
</template>

<script >
import treelist from "./treelist.vue"
	export default {
		props:{
			tree:{
				default:[]
			}
		},
		data(){
			return {
			}
		},
		components:{
			treelist
		}

	}
</script>

<style scoped>
    .tree-menu {
    	width: 360px;
    	height: 100%;
    	padding: 0 12px;
    	margin: 0 auto;
    	/*border: 1px solid #e6e9f0;*/
    }
    .tree-menu-comm span {
    	display: block;
    	font-size: 12px;
    	position: relative; 
    }
    .tree-menu-comm span strong{
    	display: block;
    	width:82%;
    	position: relative;
    	line-height: 22px;
    	padding: 2px 0;
    	padding-left: 5px;
    	color: #161719;
    	font-weight: normal;
    }
    .trre-nav{
    	background-color: #e7f2fe;
    	border: 1px solid #bfdaf4;
    	padding-left: 14px;
    	margin-left: 0;
    }
    .tree-title{
    	border: 1px solid #fff;
    	margin-top: 1px;
    }
    .ico {

    }
</style>