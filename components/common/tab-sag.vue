<template>
	<view class="tag icon iconfont" :class="[sex == 0?' icon-nan bg1' : ' icon-nv bg']">{{age}}</view>
</template>

<script>
	export default{
		props:{
			sex:Number,
			age:Number
		}
	}
</script>

<style lang="scss" scoped>
	.tag{
		color: #FFFFFF;
		font-size: 23rpx;
		padding: 2rpx 10rpx;
		margin-left: 10rpx;
		border-radius: 20rpx;
		line-height: 24rpx;
	}
	.bg{
		background-color: pink;
		
	}
	.bg1{
			background-color: #007AFF;
	}
</style>
