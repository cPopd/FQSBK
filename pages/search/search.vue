<template>
	<view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		},
		//监听原生状态栏 取消按钮事件
		onNavigationBarButtonTap(e) {
			uni.navigateBack({
				delta:1
			})
		},
		//监听搜索框的值
		onNavigationBarSearchInputChanged(e) {
			console.log(e.text)
		},
		//监听用户键盘搜索事件
		onNavigationBarSearchInputConfirmed() {
			console.log(e.text)
		}
	}
</script>

<style>

</style>
