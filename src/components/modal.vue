<template>
	<div class="modal">
		<div class="modal-header">
			<h4>{{modalTitle}}</h4>
		</div>
		<div class="modal-content">
			<div>
				<slot name="modal-content">在这里添加内容</slot>
			</div>
		</div>
		<div class="modal-foot">
			<slot name="modal-foot">
				<input class="btn" type="button" value="取消" @click="cancel" />
				<input class="btn blue" type="button" value="确定" @click="confirm" />
			</slot>
		</div>
	</div>
</template>

<script >
	export default {
		props:{
			modalTitle:{
				type:String,
				default:"这是一个模态框"
			}
		},
		methods:{
			cancel(){
				this.$emit("cancel")
			},
			confirm(){
				this.$emit("confirm")
			}
		}

	}
</script>

<style scoped>
.modal {
	width: 300px;
	margin: 0 auto;
	border-radius: 10px;
	box-shadow: 1px 1px 5px #999;
	overflow: hidden;
}
.modal-header h4{
	text-align: left;
	text-indent: 20px;
	padding:5px 0;
	font-weight: bold;
	border-bottom: 1px solid #ccc;
}
.modal-content {
	padding: 10px 0;
	border-bottom: 1px solid #eee;
}
.modal-foot .btn{
	background-color: #ccc;
	border: none;
	padding: 6px 12px;
	cursor: pointer;
	margin: 10px 5px;
	float: right;
	outline: none;
}
.modal-foot .blue{
	background-color: #37cbf9!important;
}
    
</style>