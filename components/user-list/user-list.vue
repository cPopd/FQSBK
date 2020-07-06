<template>
	<view>
		
					 <view class="user-list u-f-ac">
					 			 <!-- 左边-->
					 			 <image :src="item.userpic" mode="aspectFill" lazy-load></image>
					 			 <!-- 右边-->
					 			 <view class="list-d u-f-ajc">
					 				 <view class="list-nic">
					 				 	<view>
					 				 		{{item.username}}	<tab-sag :age="item.age" :sex="item.sex" style="width: 50rpx;"></tab-sag>
					 				 	</view>
					 				 </view>
					 			 <view class="list-y">
					 			 <view class="icon iconfont icon-xuanze-yixuan" v-if="item.isguanzhu"></view>
					 				<view class="icon iconfont icon-zengjia1" style="color: #F8791B;" v-else></view>
					 			 </view>
					 			 </view>
					 </view>
	
	</view>
</template>

<script>
	import tabSag from "../../components/common/tab-sag.vue";
	export default{
		props:{
			item:Object,
			index:Number
		},
		components:{
			tabSag
		}
	}
</script>

<style lang="scss" scoped>
	.user-list{
		padding: 20rpx 0;
		border-bottom: 1rpx solid #EEEEEE;
		image{
			width: 100rpx;
			height: 100rpx;
			border-radius: 100%;
			margin-right: 20rpx;
			flex-shrink: 0;
		}
	}
	.list-nic{
		flex: 1;
	}
	.list-y{
		width: 80rpx;
	}
	.list-d{
		flex: 1;
	}
</style>
