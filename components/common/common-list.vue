<template>
	<view class="common-list u-f animated fadeInLeft fast">
		<!-- 左边 -->
		<view>
			<view class="common-list-l">
				<image :src="item.userpic" mode="widthFix" lazy-load></image>
			</view>
		</view>
		<!-- 右边 -->
		<view class="common-list-r">
			<!-- 昵称 等 -->
			<view class="u-f-ac u-f-jsb">
				<view class="common-list-r-z u-f-ac">
					{{item.username}}
				<view class="tag icon iconfont" :class="[item.sex == 0?' icon-nan bg1' : ' icon-nv bg']">{{item.age}}</view>
				</view>
				<view class="icon iconfont icon-zengjia" v-show="!isguanzhu" @tap="guanzhu">关注</view>
			</view>
			<!-- 标题 -->
			<view>
				{{item.title}}
			</view>
			<view class="u-f-ajc">
				<!-- 图片 -->
				<image :src="item.titlepic" v-if="item.titlepic != ''" mode="widthFix" lazy-load></image>
				<!-- 视频 -->
				<view class="common-list-play icon iconfont icon-bofang" v-if="item.video">
					
				</view>
					<view class="common-list-playinfo" v-if="item.video">
						{{item.video.looknum}}次播放 {{item.video.long}}
					</view>
				<!-- 分享 -->
				<view class="common-list-share u-f-ac" v-if="item.share">
					<image :src="item.share.titlepic" mode="widthFix" lazy-load></image>
					<view class="">
						{{item.share.title}}
					</view>
				</view>
			</view>
			<!-- 地址点赞 等 -->
			<view class="u-f-ac u-f-jsb">
				<view>{{item.path}}</view>
				<view class="u-f-ac">
					<view class="icon iconfont icon-zhuanfa">{{item.sharenum}}</view>
					<view class="icon iconfont icon-pinglun1">{{item.commentnum}}</view>
					<view class="icon iconfont icon-dianzan1" style="margin-top: 4rpx;">{{item.goodnum}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			item:Object,
			index:Number
		},
		data() {
			return{
				isguanzhu : this.item.isguanzhu
			}
		},
		methods:{
			guanzhu(){
				this.isguanzhu = true
				uni.showToast({
					title: '关注成功'
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	.nav-right{
		width: 80%;
		view{
			font-size: 42rpx;
		}
	}
	.nav-left{
		margin-left: 30rpx;
		view{
			font-size: 42rpx;
			color: #ff9619;
		}
	}
	.nav-tab-bar{
		width: 100%;
		margin-left: -20rpx;
		position: relative;
		view{
			font-size: 32rpx;
			padding: 0 15rpx;
			font-weight: bold;
			color: #969696;
		}
	}
	.nav-tab-bar-line{
			position: absolute;
			border-bottom: 12rpx solid #ffff00;
			width: 40rpx;
			border-radius: 20rpx;
			bottom: -6rpx;
	}
	.activ{
			color: #333333 !important; 
		}
		
		.common-list{
			padding: 25rpx;	
		}
		.common-list-l{
			flex-shrink: 0;
			image{
				width: 90rpx;
				height: 90rpx;
				border-radius: 100%;
			}
		}
		.common-list-r{
			flex: 1;
			margin-left: 15rpx;
			border-bottom: 1rpx solid #EEEEEE;
			padding-bottom: 10rpx;
			image{
				width: 100%;
				border-radius: 10rpx;
			}
			.tag{
				color: #FFFFFF;
				font-size: 23rpx;
				padding: 2rpx 10rpx;
				margin-left: 10rpx;
				border-radius: 20rpx;
				line-height: 24rpx;
			}
		}
		.bg{
			background-color: pink;
			
		}
		.bg1{
				background-color: #007AFF;
		}
	
		.common-list-r>view:nth-child(1)>view:first-child{
			color: #999999;
			font-size: 30rpx;
		}
		.common-list-r>view:nth-child(1)>view:last-child{
			background-color: #EEEEEE;
			padding: 0 20rpx;
			font-size: 26rpx;
		}
		.common-list-r>view:nth-child(2){
			font-size: 32rpx;
			padding: 12rpx 0;
		}
		.common-list-r>view:nth-child(3){
			position: relative;
		}
		.common-list-play,.common-list-playinfo{
			position: absolute;
		}
		.common-list-playinfo{
			right: 10rpx;
			bottom: 10rpx;
			background-color: rgba(51,51,51,0.7);
			border-radius: 22rpx;
			padding: 0 15rpx;
			font-size: 26rpx;
			color: #FFFFFF;
		}
		.common-list-play{
			color: #EEEEEE;
			font-size: 100rpx;
		}
		.common-list-r>view:nth-child(4)>view{
			color: #AAAAAA;
		}
		.common-list-r>view:nth-child(4)>view:nth-child(2)>view{
			margin-left: 20rpx;
			padding-left: 5rpx;
			font-size: 26rpx;
			margin-top: 10rpx;
		}
		
		.common-list-share{
			background-color: #EEEEEE;
			width: 100%;
			padding: 10rpx;
			border-radius: 10rpx;
			image{
				width: 200rpx;
				height: 150rpx;
				margin-right: 10rpx;
			}
		}
</style>
