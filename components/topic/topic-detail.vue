<template>
	<view>
		<view class="topic-bg">
			<image :src="item.titlepic" mode="widthFix" lazy-load></image>
		</view>
		<!-- 话题信息 -->
		<view class="topic-top">
			<view class="topic-a u-f-ac">
				<image :src="item.titlepic"
				 mode=" aspectFill" lazy-load></image>
				 <view>#{{item.titile}}#</view>
			</view>
			<view class="topic-b u-f-ac">
				<view>动态 {{item.todaynum}}</view>
				<view>今日 {{item.totalnum}}</view>
			</view>
			<view class="topic-c">
				{{item.desc}}
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
			
		},
		props:{
			item:Object
		}
	}
</script>

<style lang="scss" scoped>
.topic-bg{
	width: 100%;
	height: 300rpx;
	position: relative;
	overflow: hidden;//超出部分隐藏
	image{
			width: 100%;
			position: absolute;
			filter: blur(10px);
		}
}
.topic-top{
	padding: 0 25rpx;
}
.topic-a{
	position: relative;
	image{
		width: 150rpx;
		height: 150rpx;
		border-radius: 20rpx;
		position: absolute;
		top: -75rpx;
	}
	view{
		font-size: 35rpx;
		margin-left: 160rpx;
		flex: 1;
		color: #333333;
	}
}
.topic-b{
	padding: 35rpx 0 15rpx 0;
	view{
		color:#CDCDCD;
	}
}
.topic-c{
	color:#A3A3A3;
	font-size: 32rpx;
	padding-bottom: 10rpx;
	
}
</style>
