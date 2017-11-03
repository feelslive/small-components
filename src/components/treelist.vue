<template>
	<ul id="treelist">
		<li  v-for="item in trees">
			<div class="tree-title" :style="[stylepad]">
				<span>
					<strong>{{item.title}}</strong>
					<i class="ico"></i>
				</span>
			</div>
			<!-- 组件自己调用自己*递归组件 -->
			<treelist v-if="item.chindren" :incount="count" :trees="item.chindren"></treelist>
		</li>
	</ul>
	
</template>

<script >
	import treelist from "./treelist.vue"
	export default {
		name:"treelist",
		props:{
			trees:{
				type:Array,
				default:[]
			},
			incount:{
				type:Number,
				default:0
			}
		},
		computed:{
			count(){
				var c = this.incount;
				return ++c;
			},
			stylepad(){
				return{
					'padding-left':this.count*16+"px"
				}
			}
		},
		components:{
			treelist
		}

	}
</script>

<style scoped>
    #treelist{
    	text-align: left;
    }
</style>