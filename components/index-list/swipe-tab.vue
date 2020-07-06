<template>
	<view>
		<view class="uni-tab-bar">
			<scroll-view scroll-x class="uni-swiper-tab" :style="scrollStrle">
				<block v-for="(tab,i) in tabBars" :key="i">
					<view class="swiper-tab-list" style="width: 32%;"
					 :class="{'active animated pulse' : tabIndex == i}"
					 @tap="tabtap(i)" :style="scrollItemStrle"
					 >
						{{tab.name}} {{tab.num?tab.num:''}}
					</view>
				</block>
			</scroll-view>
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
			tabtap(e){
				this.$emit('tabtap',e)
			}
		},
		props:{
			tabBars:Array,
			tabIndex:Number,
			scrollStrle:{
				type:String,
				default:""
			},
			scrollItemStrle:{
				type:String,
				default:""
			}
		}
	}
</script>

<style lang="scss">
.swiper-tab-list{
	color: #969696;
	font-weight: bold;
}
.uni-swiper-tab{
	border-bottom: 1rpx solid #EEEEEE;
}
.uni-tab-bar .active{
	color: #343434;
	border-bottom: 6rpx solid #FEDE33;
	width: 100rpx ;
	margin-left: 10rpx;
}
</style>
