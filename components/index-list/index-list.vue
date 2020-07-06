<template>
	<view>
		<view class="index-list animated fadeInLeft fast">
			<!-- 个人信息栏 -->
			<view class="index-list1">
				<view class="index-list1-1">
					<image lazy-load :src="item.userpic" mode="widthFix"></image>
					{{item.username}}
				</view>
				<view class="index-list1-2" v-if="!isguanzhu" @tap="guanzhu">
					<view class="icon iconfont icon-zengjia"></view>
					<view>关注</view>  
				</view>
			</view>
			<!-- 标题栏 -->
			<view class="index-list2" @tap="opentetail">{{item.title}}</view>
			<!-- 主要图文 -->
			<view class="index-list3 u-f-ajc" hover-class="animated pulse" hover-stay-time="800">
				<image lazy-load :src="item.titlepic" mode="widthFix" @tap="opentetail"></image>
				<!-- 视频 -->
				<view class="incn iconfont icon-bofang index-list3-1" v-if="item.type=='video'"></view>
				<!-- 播放信息 -->
				<view class="index-list3-2" v-if="item.type=='video'">20W次播放 2:35</view>
			</view>
			<!-- 评论转发等 -->
			<view class="index-list4">
				<view class="index-list4-1">
					<view @tap="dianzan(item,index)" :class="infonum.index == 1 ? 'x_active animated fadeInLeft':''">
						<view class="icon iconfont icon-icon_xiaolian-mian" :class="infonum.index == 1 ? 'x_active animated fadeInLeft':''"></view>
						{{infonum.dingnum}}
					</view>
					<view @tap="diancai(item,index)" :class="infonum.index == 2 ? 'x_active animated fadeInRight':''">
						<view class="icon iconfont icon-kulian" :class="infonum.index == 2 ? 'x_active animated fadeInRight':''"></view>
						{{infonum.cainum}}
					</view> 
				</view>
				<view class="index-list4-2">
					<view>
						<view class="icon iconfont icon-pinglun1"></view>
						{{item.commentnum}}
					</view>
					<view>
						<view class="icon iconfont icon-zhuanfa"></view>
						{{item.sharenum}}
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				 isguanzhu : this.item.isguanzhu,
				 infonum: this.item.infonum,
				 c1:false
			}
		},
		methods: {
			dianzan(e){
				if(this.infonum.index == 2){
					this.infonum.cainum = this.infonum.cainum - 1
					this.infonum.index = 1
					this.infonum.dingnum = this.infonum.dingnum + 1
					return
				}
				if(this.infonum.index == 0){
					this.infonum.index = 1
					this.infonum.dingnum = parseInt(this.infonum.dingnum) + 1
					console.log(this.infonum.dingnum)
				}else{
					this.infonum.index = 0
					this.infonum.dingnum = this.infonum.dingnum - 1
				}
				
			},
			diancai(e){
				if(this.infonum.index == 1){
					this.infonum.dingnum = this.infonum.dingnum - 1
					this.infonum.index = 2
					this.infonum.cainum = this.infonum.cainum + 1
					return
				}
				if(this.infonum.index == 0){
					this.infonum.index = 2
					this.infonum.cainum = this.infonum.cainum + 1
				}
				else{
					this.infonum.index = 0
					this.infonum.cainum = this.infonum.cainum - 1
				}
			},
			//关注事件
			guanzhu(){
				this.isguanzhu = true
				uni.showToast({
					title:'关注成功',
					icon:'success'
				})
			},
			//进入详情页面
			opentetail(){
				
			},
			dongtai(e){
				this.c1 = !this.c1
			}
		},
		props:{
			item:Object,
			index:Number
		}
	}
</script>

<style lang="scss" scoped>
.index-list {
	padding: 20rpx;
	border-bottom: 1rpx solid #eeeeee;
	.index-list1 {
		@extend %flex-between-center;
		.index-list1-1 {
			display: flex;
			align-items: center;
			color: #999999;
			image {
				width: 90rpx;
				height: 90rpx;
				border-radius: 100%;
				margin-right: 10rpx;
			}
		}
		.index-list1-2 {
			width: 100rpx;
			text-align: center;
			display: flex;
			align-items: center;
			background-color: #f4f4f4;
			border-radius: 5rpx;
			padding-left: 10rpx;
		}
	}
	.index-list2 {
		padding-top: 15rpx;
	}
	.index-list3 {
		padding-top: 15rpx;
		position: relative;
		image {
			width: 100%;
			border-radius: 20rpx;
		}
		.index-list3-1 {
			position: absolute;
			font-size: 80rpx;
			color: #ffffff;
		}
		.index-list3-2 {
			position: absolute;
			color: #ffffff;
			background-color: rgba($color: #000000, $alpha: 0.4);
			border-radius: 40rpx;
			bottom: 8rpx;
			right: 8rpx;
			font-size: 22rpx;
			padding: 0 12rpx;
		}
	}
	.index-list4 {
		@extend %flex-between-center;
		padding: 15rpx 0;
		color: #999999;
		.index-list4-1 {
			display: flex;
			align-items: center;
			view {
				margin-right: 10rpx;
			}
		}
		.index-list4-2 {
			display: flex;
			align-items: center;
			view {
				margin-right: 10rpx;
			}
		}
		view {
			display: flex;
			align-items: center;
		}
	}
}
.x_active{
	color: #C5F61C;
}
</style>
