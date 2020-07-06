<template>
	<view>
		<view class="paper-mask" v-show="show" @tap="hidepopup"></view>
			<view class="paper-left">
				<view class="u-f-ac" hover-class="back animated bounceOut" hover-stay-time="1000" v-show="show" @click="addfriend">
					<view class="icon iconfont icon-sousuo">
					</view>加糗友</view>
				<view class="u-f-ac" hover-class="back animated bounceOut" hover-stay-time="1000" v-show="show" @click="clear">
					<view class="icon iconfont icon-qingchu"></view>清除缓存</view>
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
			hidepopup(){
				this.$emit('hide');
			},
			addfriend(){
				this.$emit('addfriend');
			},
			clear(){
				this.$emit('clear');
			}
		},
		props:{
			show:Boolean
		}
	}
</script>

<style lang="scss">
.paper-left{
	position: fixed;
	right: 0;
	top: 10rpx;
	background-color: #FFFFFF;
	z-index: 2000;
	width: 55%;
	box-shadow: 1rpx 1rpx 20rpx 2rpx #CCCCCC;
	view{
		padding: 20rpx;
		font-size: 35rpx;
		view{
			font-weight: bold;
		}
	}
}
.back{
	background-color: #CCCCCC;
}
	.paper-mask{
		position: fixed;
		right: 0;
		left: 0;
		top: 0;
		bottom: 0;
		z-index: 1999;
	}
</style>
