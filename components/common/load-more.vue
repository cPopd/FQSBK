<template>
	<view class="load-moer">
		{{loadtext}} <!-- 上拉加载更多-->
	</view>
</template>

<script>
	export default{
		props:{
			 loadtext:String
		}
	}
</script>

<style lang="scss" scoped>
	.load-moer{
		padding: 15rpx;
		text-align: center;
		color: #aaaaaa;
	}
	
</style>
