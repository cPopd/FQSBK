<template>
	<view class="body">
		<!-- 头部边框 -->
		<view style="border-bottom: 1rpx solid #EFEFEF;">
		</view>
		<!-- 主体内容 -->
		<configList @tap="gopage(index)" :datalist="datalist"></configList>
		<!-- 退出登录 -->
		<view class="bom u-f-ajc" hover-class="animated pulse" hover-stay-time="200">
			退出登录
		</view>
	</view>
</template>

<script>
	import configList from '../../components/configList/configList.vue';
	export default {
		data() {
			return {
				datalist:[
					{
						name:'账号与安全',
						url:'xiugaimima'
					},
					{
						name:'绑定邮箱',
						url:'bangding'
					},
					{
						name:'编辑资料',
						url:'update'
					},
					{
						name:'小字条',
						url:''
					},
					{
						name:'清楚缓存',
						url:''
					},
					{
						name:'意见反馈',
						url:'yijianfankui'
					},
					{
						name:'关于糗事百科',
						url:'guanyu'
					}
				]
			}
		},
		methods: {
			gopage(index){
				var url = "";
				switch(index){
					case 0:
					url = "账号与安全"
					break;
					case 1:
					url = "绑定邮箱"
					break;
					case 2:
					url = "绑定邮箱"
					break;
					case 3:
					url = "绑定邮箱"
					break;
					case 4:
					url = "绑定邮箱"
					break;
					case 5:
					url = "绑定邮箱"
					break;
					case 6:
					url = "guanyu"
					break;
				}
				console.log(url)
				uni.navigateTo({
					url:url
				})
			}
		},
		components:{
			configList
		}
	}
</script>

<style lang="scss" scoped>
.body{
	padding: 30rpx 30rpx;
}
.bom{
	background-color: #FFE933;
	color: #333333;
	width: 100%;
	height: 100rpx;
	border-radius: 10rpx;
	font-size: 34rpx;
	font-weight: 600;
	margin-top: 30rpx;
}
</style>
