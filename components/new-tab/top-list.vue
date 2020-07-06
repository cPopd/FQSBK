<template>
	<view>
		
		<view class="topic-new animated fadeInLeft fast" @tap="gopage">
			<view class="new">最近更新</view>
				<block v-for="(item,index) in list" :key="index">
					<view class="list u-f animated fadeInLeft fast">
					<image :src="item.titlepic"
					mode="widthFix" lazy-load hover-class="animated pulse" hover-stay-time="800"></image>
					<view>
						<view>#{{item.title}}#</view>
						<view>{{item.desc}}</view>
						<view>动态{{item.totalnum}} 今日{{item.todaynum}}</view>
					</view>
					</view>
				</block>
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
					url:'../../pages/topic-detail/topic-detail'
				})
			}
		}, 
		props:{
			list:Array
		}
	}
</script>

<style lang="scss">
.topic-new{
	padding: 20rpx;
	border-bottom: 1rpx solid #EEEEEE;
	.new{
		padding-bottom: 10rpx;
		font-size: 28rpx;
	}
	.list{
		padding: 10rpx 0;
		image{
			width: 150rpx;
			height: 150rpx;
			border-radius: 10rpx;
			margin-right: 20rpx;
		}
	}
}
.topic-new>view>view{
	color: #A4A4A4;
	}
.list>view>view:first-child{
	color: #333333;
	font-size: 32rpx;
}
</style>
