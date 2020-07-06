<template>
	<view class="body">
		<!-- 未登录显示 -->
		<view class="top_top" v-if="!isdenglu">
			<view style="text-align: center; font-size: 28rpx; color: #4d4d4d;;">
				登录糗事百科,体验更多功能
			</view>
			<view class="tow u-f-ajc">
				<view class="u-f-ajc icon iconfont icon-weixin" style="background-color: #2BD19B;">
				</view>
				<view class="u-f-ajc icon iconfont icon-QQ" style="background-color: #2CAEFC;"></view>
				<view class="u-f-ajc icon iconfont icon-xinlangweibo" style="background-color: #FC7729;"></view>
			</view>
			<view class="u-f-ajc" @click="paeego">
				<view class="login">账号密码登录</view>
				<view class="login2 icon iconfont icon-jinru"></view>
			</view>
		</view>
		<!-- 头像 -->
		<view class="top u-f" v-if="isdenglu" @click="gopage('../usermin/usermin')">
			<image src="../../static/datapic/10.jpg" mode="aspectFill" lazy-load></image>
			<!-- 名字 访客等 -->
			<view class="top_list">
				<view class="name">威风</view>
				<view class="neirong">总访客 0 今日 0</view>
			</view>
			<view class="top_jiantou u-f-ajc icon iconfont icon-jinru">
			</view>
		</view>
		<!-- 动态详情 -->
		<view class="mid u-f">
			<block v-for="(item,index) in midlist" :key="index">
				<view>
					<view class="mid_top u-f-ajc">
						{{item.num}}
					</view>
					<view class="mid_bom u-f-ajc">
						{{item.neirong}}
					</view>
				</view>
			</block>
		</view>
		<!-- 广告位 -->
		<view class="guanggao">
			<image src="../../static/datapic/26.jpg" lazy-load mode=" widthFix" class="topimg"></image>
		</view>
		<!-- 导航条 -->
		<!-- 浏览历史 -->
		<view class="top_daohang u-f-ajc">
			<view class="a icon iconfont icon-liulan"></view>
			<view class="b">浏览历史</view>
			<view class="c iconfont icon-jinru"></view>
		</view>
		<!-- 糗事百科 -->
		<view class="top_daohang u-f-ajc">
			<view class="a icon iconfont icon-huiyuanvip" style="color: #FF7434;"></view>
			<view class="b">糗事百科</view>
			<view class="c iconfont icon-jinru"></view>
		</view>
		<!-- 审核糗事 -->
		<view class="top_daohang u-f-ajc">
			<view class="a icon iconfont icon-icon_im_keyboard"></view>
			<view class="b">审核糗事</view>
			<view class="c iconfont icon-jinru"></view>
		</view>
		<!-- 设置 -->
		<view class="top_daohang u-f-ajc" v-if="isdenglu" @click="gopage('config')">
			<view class="a icon iconfont icon-shezhi" style="color: #888888;"></view>
			<view class="b">设置</view>
			<view class="c iconfont icon-jinru"></view>
		</view>
		
		<!-- 切换测试 -->
		 <view style="margin-top: 30rpx;"> 
			<button @click="qiehuan">点击切换已登录状态</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				midlist:[
					{
						num:0,
						neirong:'糗事'
					},
					{
						num:0,
						neirong:'动态'
					},
					{
						num:0,
						neirong:'评论'
					},
					{
						num:0,
						neirong:'收藏'
					}
				],
				isdenglu:false
			}
		},
		methods: {
			qiehuan(){
				this.isdenglu=!this.isdenglu
			},
			paeego(){
				uni.navigateTo({
					url:'../login/login'
				})
			},
			gopage(e){
				uni.navigateTo({
					url:e
				})
			}
		}
	}
</script>

<style lang="scss">
.body{
	padding: 30rpx;
}
.top{
	image{
		width: 130rpx;
		height: 130rpx;
		border-radius: 100%;
	}
	.top_list{
		margin-left: 30rpx;
		width: 70%;
		.name{
			font-size: 36rpx;
			font-weight: 400;
		}
		.neirong{
			color: #A4A4A4;
			font-size: 28rpx;
		}
	}
}
.mid{
	width: 100%;
	 flex-direction:row;
	 padding-top: 20rpx;
	.mid_top{
		font-size: 36rpx;
		width: 180rpx;
	}
	.mid_bom{
		width: 180rpx;
		font-size: 30rpx;
		color: #A4A4A4;
		margin-top: -10rpx;
	}
}
.topimg{
	width: 100%;
	height: 200rpx;
	border-radius: 20rpx;
}
.top_daohang{
	padding:0 30rpx;
	height: 100rpx;
	border-bottom: 1rpx solid #F1F1F1;
	.a{
		width: 5%;
		color: #44B3FF;
		font-size: 40rpx;
	}
	.b{
		font-size: 28rpx;
		width: 90%;
		margin-left: 30rpx;
	}
	.c{
		width: 5%;
	}
}
.top_top{
	 flex-direction:row;
	 .tow{
		 padding: 30rpx 0;
		 view{
			 
			 font-size: 40rpx;
			 margin: 0 50rpx;
			 background-color: #09BB07;
			 border-radius: 50%;
			 width: 100rpx;
			 height: 100rpx;
			 color: #FFFFFF;
		 }
	 }
	 .login{
		 font-size: 28rpx;
		 color: #4d4d4d;
	 }
	 .login2{
		 font-size: 40rpx;
		 color: #E9E9E9;
	 }
}
.guanggao{
	padding: 20rpx 0;
	border-bottom: 1rpx solid #F1F1F1;
}
</style>
