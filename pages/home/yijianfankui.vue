<template>
	<view class="body">
		<!-- :class="infonum.index == 1 ? 'x_active animated fadeInLeft':''"> -->
		<view v-for="(item,index) in datalist" :key="index" @click="iszhankai(item)">
			<view class="top u-f-ajc u-f-jsb">
				{{item.name}}
				<view class="icon iconfont icon-jinru" :class="item.isxiala ? 'icon iconfont icon-xialazhankai' : ''"></view>
			</view>
			<view class="font animated bounceInLeft" v-show="item.isxiala">
				{{item.title}}
				<br />
				<br />
				PS.紧急问题及时进行反馈
			</view>
		</view>
		<button class="bom u-f-ajc" hover-class="animated pulse" hover-stay-time="200">
			意见反馈
		</button>
	</view>
</template>

<script>
export default {
	data() {
		return {
			isxiala: true,
			datalist:[
				{
					name:'客服什么时候在线?',
					title:'亲爱的XXX，客服的工作时间是阿萨德破解器我就打什么的爱是浦东考勤瓦斯的行情哇视频动机企鹅哦IP静安寺打破近千万',
					isxiala:false
				},
				{
					name:'忘记账号/昵称/密码怎么办?',
					title:'亲爱的XXX，客服的工作时间是阿萨德破解器我就打什么的爱是浦东考勤瓦斯的行情哇视频动机企鹅哦IP静安寺打破近千万',
					isxiala:false
				},
				{
					name:'怎么搜索/查找、关注/取关用户?',
					title:'亲爱的XXX，客服的工作时间是阿萨德破解器我就打什么的爱是浦东考勤瓦斯的行情哇视频动机企鹅哦IP静安寺打破近千万',
					isxiala:false
				}
			]
		};
	},
	methods: {
		iszhankai(item) {
			item.isxiala = !item.isxiala
		}
	}
};
</script>

<style lang="scss" scoped>
.body {
	padding: 20rpx;
}
.top {
	width: 100%;
	height: 100rpx;
	font-size: 30rpx;
}
.font {
	color: #666666;
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
