<template>
	<view>
		<block v-for="(item,index) in datalist" :key="index">
		<view class="top u-f-ajc u-f-jsb" @click="gopage(index,item)" hover-class="animated pulse" hover-stay-time="200">
			{{item.name}}
			<view class="icon iconfont icon-jinru"></view>
		</view>
		</block>
	</view>
</template>

<script>
	export default {   
		data() {
			return {
				
			} 
		},
		methods: {
			gopage(index,item){
				/* if(item.url=='guanyu1'){
					console.log('退出')
				} */
				uni.navigateTo({
					url:item.url
				})
			}
		},
		props:{
			datalist:Array
		}
	}
</script>

<style lang="scss" scoped>
.top{
	width: 100%;
	height: 100rpx;
	border-bottom: 1rpx solid #EFEFEF;
	font-size: 30rpx;
}
</style>
