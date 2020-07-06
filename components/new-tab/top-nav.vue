<template>
	<view>
		<view class="topic-nav">
			<!-- 热门分类 -->
			<view class="u-f-ac u-f-jsb">
				<view style="color: #000000;">热门分类</view>
				<view class="u-f-ajc" @tap="gopage">更多
				<view class="icon iconfont icon-jinru">
				</view>
				</view>
			</view>
			<!-- 更多 -->
			<view class="u-f-ac" >
				<view v-for="(item,index) in fenlei" :key="index">{{item.name}}</view>
			</view>
		</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			gopage(){
				uni.navigateTo({
					url:'../../pages/topic-nav/topic-nav'
				})
			}
		},
		props:{
			fenlei:Array
		}
	}
</script>

<style lang="scss" scoped>

	.topic-nav{
		border-bottom: 1rpx solid #EEEEEE;
		border-top: 1rpx solid #EEEEEE;
		padding: 20rpx;
	}
	.topic-nav>view:first-child{
		margin-bottom: 10rpx;
		view{
			color: #9E9E9E;
		}
	}
	.topic-nav>view:last-child{
		
		view{
			flex:1;
			background-color: #dddddd;
			color: #9E9E9E;
			border-radius: 10rpx;
			margin: 0 10rpx;
			text-align: center;
		}
	}
</style>
