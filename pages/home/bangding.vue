<template>
	<view class="body">
		<input class="clsinput u-f-ajc" @input="a" placeholder="输入邮箱" />
		<input class="clsinput u-f-ajc" @input="a" password placeholder="请输入密码" />
		<button class="u-f-ajc" style="margin-top: 40rpx; background-color: #FFE933;">完成</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			a(e){
				console.log(e.detail.value)
			}
		}
	}
</script>

<style lang="scss" scoped>
.body{
	padding: 30rpx;
}
.clsinput{
	border-bottom: 1rpx solid #EFEFEF;
	height: 80rpx;
	width: 100%;
}
</style>
