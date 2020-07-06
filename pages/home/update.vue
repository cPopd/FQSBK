<template>
	<view class="body">
		<!-- 头像 -->
		<view class="top u-f-ajc u-f-jsb">
			<view class="top_text">头像</view>
			<view class="top_right u-f">
				<view><image src="../../static/userpic/14.jpg" mode="aspectFill" lazy-load></image></view>
				<view class="u-f-ajc icon iconfont icon-bianji1" style="color: #BEBEBE;"></view>
			</view>
		</view>
		<!-- 昵称 -->
		<view class="top u-f-ajc u-f-jsb">
			<view class="top_text">昵称</view>
			<view class="top_right u-f">
				<view class="maright"><input :value="oldname" @input="newname" /></view>
				<view class="u-f-ajc icon iconfont icon-bianji1" style="color: #BEBEBE;"></view>
			</view>
		</view>
		<!-- 性别 -->
		<view class="top u-f-ajc u-f-jsb">
			<view class="top_text">性别</view>
			<view class="top_right u-f">
				<view class="maright">
					<picker @change="bindPickerChange" :value="index" :range="array" range-key="name">
						<view class="uni-input">{{ array[index].name }}</view>
					</picker>
				</view>
				<view class="u-f-ajc icon iconfont icon-bianji1" style="color: #BEBEBE;"></view>
			</view>
		</view>
		<!-- 生日 -->
		<view class="top u-f-ajc u-f-jsb">
			<view class="top_text">生日</view>
			<view class="top_right u-f">
				<view class="maright">
					<picker mode="date" :value="date" @change="bindDateChange">
						<view class="uni-input">{{ date }}</view>
					</picker>
				</view>
				<view class="u-f-ajc icon iconfont icon-bianji1" style="color: #BEBEBE;"></view>
			</view>
		</view>
		<!-- 婚姻状态 -->
		<view class="top u-f-ajc u-f-jsb">
			<view class="top_text">情感</view>
			<view class="top_right u-f">
				<view class="maright">
					<picker @change="bindPickerChange1" :value="index1" :range="array1" range-key="name">
						<view class="uni-input">{{ array1[index1].name }}</view>
					</picker>
				</view>
				<view class="u-f-ajc icon iconfont icon-bianji1" style="color: #BEBEBE;"></view>
			</view>
		</view>
		<!-- 职业 -->
		<view class="top u-f-ajc u-f-jsb">
			<view class="top_text">职业</view>
			<view class="top_right u-f">
				<view class="maright"><input :value="zhiye" @input="newname" /></view>
				<view class="u-f-ajc icon iconfont icon-bianji1" style="color: #BEBEBE;"></view>
			</view>
		</view>
		<!-- 地区选择 -->
		<pick-regions :defaultRegion="defaultRegionCode" @getRegion="handleGetRegion">
			<view class="top u-f-ajc u-f-jsb">
				<view class="top_text">家乡</view>
				<view class="top_right u-f">
					<view class="maright">{{ diqv }}</view>
					<view class="u-f-ajc icon iconfont icon-bianji1" style="color: #BEBEBE;"></view>
				</view>
			</view>
		</pick-regions>
		
		<button class="u-f-ajc" style="margin-top: 40rpx; background-color: #FFE933;" hover-class="animated pulse" hover-stay-time="200">完成</button>
		
	</view>
</template>

<script>
import pickRegions from '@/components/pick-regions/pick-regions.vue';
export default {
	data() {
		return {
			date: '1998-01-21',
			array: [{ name: '男' }, { name: '女' }],
			array1: [{ name: '未婚' }, { name: '已婚' }],
			index: 0,
			index1: 0,
			oldname: '旧的名字',
			zhiye: '脑瘫前端',
			defaultRegion: ['广东省', '广州市', '番禺区'],
			defaultRegionCode: '440113',
			region: [],
			diqv:'以前的地址'
		};
	},
	methods: {
		bindDateChange(e) {
			this.date = e.detail.value;
		},
		bindPickerChange(e) {
			this.index = e.detail.value;
		},
		bindPickerChange1(e) {
			this.index1 = e.detail.value;
		},
		newname(e) {
			console.log(e);
		},
		// 获取选择的地区
		handleGetRegion(region) {
			this.region = region;
			this.diqv = this.region.map(item => item.name).join(' ')
			console.log(this.diqv)
		}
	},
	components: {
		pickRegions
	}
};
</script>

<style lang="scss" scoped>
.body {
	padding: 30rpx;
}
.top {
	border-bottom: 1rpx solid #efefef;
	height: 100rpx;
	.top_text {
		color: #cccccc;
		font-size: 32rpx;
		font-weight: bold;
	}
	.top_right {
		image {
			width: 100rpx;
			height: 100rpx;
			border-radius: 50%;
			margin-right: 20rpx;
		}
		.maright {
			font-size: 30rpx;
			margin-right: 20rpx;
			input {
				text-align: right;
			}
		}
	}
}
</style>
