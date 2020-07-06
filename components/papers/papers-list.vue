<template>
	<view>
		<block v-for="(item,index) in datalist" :key="index">
			<view class="paper-list u-f-ac animated fadeInLeft">
				<image :src="item.titlepic"
				mode="aspectFill" lazy-load
				>
				</image>
				<view>
					<view class="u-f-ajc u-f-jsb">
						{{item.name}}
						<text class="sjian">{{item.date}}</text>
					</view>
					<view class="u-f-ac u-f-jsb">
						<view class="neirong">{{item.desc}}</view>
						<template v-if="item.descnum>0">
							<uni-badge :text="item.descnum" type="error"></uni-badge>
							</template>
					</view>
				</view>
			</view>
		</block>
	</view>
</template>

<script>
	import uniBadge from "../../components/uni-badge/uni-badge.vue";
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		},
		props:{
			datalist:Array
		},
		components:{
			uniBadge
		}
	}
</script>

<style lang="scss" scoped>
page{
	padding: 0 20rpx;
}
.paper-list{
	border-bottom: 1rpx solid #EEEEEE;
	padding: 20rpx 0;
	image{
		width: 100rpx;
		height: 100rpx;
		border-radius: 100%;
		margin-right: 20rpx;
		flex-shrink: 0; //防止挤压
	} 
	view{
		flex: 1;//补充
	}
}
.sjian{
color: #CBCBCB;
font-size: 28rpx;
}
.neirong{
	color: #999999;
}
.paper-list>view>view:first-child{
	font-size: 35rpx;
}
</style>
