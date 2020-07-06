<template>
	<view class="body">
		<input class="clsinput u-f-ajc" password @input="a" placeholder="输入原始密码" />
		<input class="clsinput u-f-ajc" password placeholder="输入新密码" />
		<input class="clsinput u-f-ajc" password placeholder="确认新密码" />
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
