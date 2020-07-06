<template>
	<view class="body">
		<!-- 图片 -->
		<view class="top"><image src="../../static/banner1.jpg" lazy-load mode="aspectFill"></image></view>
		<!-- 版本号 -->
		<view class="u-f-ajc" style="color: #DADADA;">
			version 1.0.0
		</view>
		<configList :datalist="datalist"></configList>
	</view>
</template>

<script>
	import configList from '../../components/configList/configList.vue';
export default {
	data() {
		return {
			datalist:[
				{
					name:'新版本检测',
					url:'guanyu1'
				},
				{
					name:'用户协议',
					url: ''
				}
			]
		};
	},
	methods: {
		
	},
	components:{
		configList
	}
};
</script>

<style lang="scss" scoped>
.body {
	padding: 30rpx;
}
.top {
	image {
		width: 100%;
		height: 400rpx;
	}
}
</style>
