<template>
	<view>
		<view class="top_image"><image src="../../static/datapic/33.jpg" lazy-load mode="aspectFill"></image></view>
		<view class="body">
			<!-- 手机登录 -->
			<block v-if="phlogin">
				<!-- 手机号码 -->
				<view class="top_content u-f-ajc">
					<view class="left">+86</view>
					<input placeholder="输入手机号码" placeholder-class="ploinput" auto-focus="true" />
				</view>
				<!-- 验证码 -->
				<view class="top_content u-f-ajc">
					<input placeholder="请输入验证码" placeholder-class="ploinput" auto-focus="true" />
					<view class="right">获取验证码</view>
				</view>
				<button class="login">登录</button>
				<view class="u-f-ajc" style="color: #5E5E5E; margin-top: 20rpx;" @click="qiehuan">
					账号密码登录
					<view style="color: #DDDDDD;" class="icon iconfont icon-jinru"></view>
				</view>
			</block>
			<!-- 账号登录 -->
			<block v-if="uslogin">
				<!-- 账号 -->
				<view class="top_content u-f-ajc">
					<input style="width: 100%;" placeholder="昵称/手机号/邮箱" placeholder-class="ploinput" auto-focus="true" />
				</view>
				<!-- 密码 -->
				<view class="top_content u-f-ajc">
					<input placeholder="请输入密码" password placeholder-class="ploinput" auto-focus="true" />
					<view style="color: #2C405A; font-size: 28rpx;width: 180rpx;">忘记密码？</view>
				</view>
				<button class="login">登录</button>
				<view class="u-f-ajc" style="color: #5E5E5E; margin-top: 20rpx;" @click="qiehuanph">
					验证码登录
					<view style="color: #DDDDDD;" class="icon iconfont icon-jinru"></view>
				</view>
			</block>

			<!-- 底部 其他登录 -->
			<view class="u-f-ajc" style="margin-top: 40rpx; color: #d5d5d5; font-size: 24rpx;">—————— 第三方登录 ——————</view>
			<!-- 外部登录 -->
			<view class="tow u-f-ajc">
				<view class="u-f-ajc icon iconfont icon-weixin" style="background-color: #2BD19B;"></view>
				<view class="u-f-ajc icon iconfont icon-QQ" style="background-color: #2CAEFC;"></view>
				<view class="u-f-ajc icon iconfont icon-xinlangweibo" style="background-color: #FC7729;"></view>
			</view>
			<!-- 协议 -->
			<view class="u-f-ajc" style="font-size: 28rpx;">注册代表您同意 <view style="color: #007AFF; font-size: 28rpx;">《二狗用户手册》</view></view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			phlogin:true,
			uslogin:false
		};
	},
	methods: {
		qiehuan(){
			if(this.phlogin){
				this.phlogin=false
				this.uslogin=!this.uslogin
			}
		},
		qiehuanph(){
			if(this.uslogin){
				this.uslogin=false
				this.phlogin=!this.phlogin
			}
		}
	}
};
</script>

<style lang="scss" scoped>
.top_image {
	image {
		width: 100%;
		height: 500rpx;
	}
}
.body {
	padding: 20rpx;
}
.top_content {
	border-bottom: 1rpx solid #efefef;
	height: 100rpx;
	.left {
		width: 80rpx;
		font-size: 30rpx;
		font-weight: bold;
	}
	input {
		width: 90%;
	}
	.right {
		width: 180rpx;
		font-size: 28rpx;
		background-color: #f4f4f4;
		color: #bbbbbb;
		text-align: center;
	}
}
.ploinput {
	color: #cbcbcb;
	font-weight: bold;
	font-size: 30rpx;
}
.login {
	color: #000000;
	background-color: #FFE933;
	margin-top: 30rpx;
}
.tow {
	padding: 30rpx 0;
	view {
		font-size: 40rpx;
		margin: 0 50rpx;
		background-color: #09bb07;
		border-radius: 50%;
		width: 100rpx;
		height: 100rpx;
		color: #ffffff;
	}
}
</style>
