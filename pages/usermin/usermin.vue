<template>
	<view>
		<!-- 背景图 -->
		<view class="top">
			<image src="../../static/datapic/28.jpg" mode="aspectFill" lazy-load></image>
			<view class="top_bom u-f-ajc">
				<view class="erer-row">
					<view>10k</view>
					<view class="huise">获赞</view>
				</view>
				<view class="erer-row">
					<view>11</view>
					<view class="huise">关注</view>
				</view>
				<view class="erer-row">
					<view>12</view>
					<view class="huise">粉丝</view>
				</view>
			</view>
		</view>
		<!-- 返回 更多按钮 -->
		<view class="tubiao u-f-ajc icon iconfont icon-fanhui" @click="fanhui">
		</view>
		<view class="tubiao2 u-f-ajc icon iconfont icon-gengduo1"  @click="isshow">
		</view>
		<!-- 点击弹出 -->
		<view class="paper-mask" v-show="show" @tap="hidepopup"></view>
		<view class="top_show erer-row animated bounceIn faster" v-if="show">
			<view class="u-f-ac" @click="lahei" hover-class="animated pulse faster">
				<view class="icon iconfont icon-sousuo"></view>
				<view style="margin-left: 20rpx;">拉黑</view>
			</view>
			<view class="u-f-ac" style="margin-top: 20rpx;" @click="beizhu" hover-class="animated pulse faster">
				<view class="icon iconfont icon-qingchu"></view>
				<view style="margin-left: 20rpx;">备注</view>
			</view>
		</view>
		<!-- 个人信息 -->
		<view class="top_mid">
			<view class="top_mida">
				<image src="../../static/datapic/21.jpg" mode="aspectFill" lazy-load></image>
			</view>
			<view class="top_midb u-f-ajc">
				<text>昵称</text><view class="u-f-ajc icon iconfont icon-nan">20</view>
			</view>
			<view class="top_midc u-f-ajc">
				+关注
			</view>
		</view>
		<!-- 滑动栏 -->
		<!-- 自定义导航栏 -->
		<swipeTab :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swipeTab>
		<!-- 列表 -->
		<view class="uni-tab-bar">
			<swiper class="swiperbody" :style="{ height: swhegiht + 'px' }" :current="tabIndex" @change="qiehuan">
				<!-- 主页内容 -->
				<swiper-item class="item-1">
					<view class="item-1-1">
						<view>账号信息</view>
						<view class="item-1-1-2">
							<view>注册年龄:1年8月6日</view>
							<view>ID:9072142</view>
						</view>
					</view>
					<view class="item-1-2">
						<view>个人信息</view>
						<view class="item-1-1-2">
							<view>星座:水瓶座</view>
							<view>职业:IT</view>
							<view>故乡:广东广州一</view>
							<view>情感状态:未婚</view>
						</view>
					</view>
				</swiper-item>
				<!-- 糗事卡 -->
				<swiper-item class="item-2">
					<scroll-view scroll-y class="list" @scrolltolower="loadmore">
						<block v-for="(item, index) in list.list" :key="index">
						<common-list :item="item" :index="index" ></common-list>
						</block>
						<!-- 上拉加载 -->
						<loadmore :loadtext="list.loadtext"></loadmore>
					</scroll-view>
				</swiper-item>
				<swiper-item>3</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import swipeTab from '../../components/index-list/swipe-tab.vue';
	import commonList from '../../components/common/common-list.vue';
	import loadmore from '../../components/common/load-more.vue';
	export default {
		data() {
			return {
			tabBars: [
				{ name: '主页', id: '0' },
				{ name: '糗事', id: '1' },
				{ name: '动态', id: '2' }
			],
			tabIndex: 0,
			swhegiht:1000,
			show:false,
			list:{
				loadtext: '上拉加载更多',
				list: [
					// 文字
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 1, //0 男 1 女
						age: 25,
						isguanzhu: true,
						title: '我是标题',
						titlepic: '',
						video: false,
						share: false,
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 1, //0 男 1 女
						age: 25,
						isguanzhu: true,
						title: '我是标题',
						titlepic: '',
						video: false,
						share: false,
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 1, //0 男 1 女
						age: 25,
						isguanzhu: true,
						title: '我是标题',
						titlepic: '',
						video: false,
						share: false,
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 1, //0 男 1 女
						age: 25,
						isguanzhu: true,
						title: '我是标题',
						titlepic: '',
						video: false,
						share: false,
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 1, //0 男 1 女
						age: 25,
						isguanzhu: true,
						title: '我是标题',
						titlepic: '',
						video: false,
						share: false,
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 1, //0 男 1 女
						age: 25,
						isguanzhu: true,
						title: '我是标题',
						titlepic: '',
						video: false,
						share: false,
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					}
					]
			}
			}
		},
		methods: {
			//点击切换
			tabtap(e) {
				this.tabIndex = e;
			},
			qiehuan(e){
				this.tabIndex = e.detail.current
			},
			fanhui(){
				uni.navigateBack({
					delta: 1
				})
			},
			/* 上拉加载 */
			loadmore(){
				if(this.list.loadtext!="上拉加载更多"){
					return;
				}
				//修改装填
				this.list.loadtext = "加载中.....";
				//获取数据
				setTimeout(()=>{
					let obj ={
							userpic: '../../static/demo7.jpg',
							username: '哈哈',
							sex: 1, //0 男 1 女
							age: 25,
							isguanzhu: true,
							title: '我是标题',
							titlepic: '',
							video: false,
							share: false,
							path: '深圳 龙岗',
							sharenum: 20,
							commentnum: 30,
							goodnum: 20
							}
					this.list.list.push(obj)
					//获取完成
					this.list.loadtext = "上拉加载更多";
				},500)
				//this.newList[e].loadtext = "没有更多数据";
			},
			isshow(){
				this.show = true
			},
			hidepopup(){
				this.show = false
			},
			lahei(){
				console.log('拉黑')
				setTimeout(()=>{
					this.hidepopup()
				},500)
			},
			beizhu(){
				console.log('备注')
				setTimeout(()=>{
					this.hidepopup()
				},500)
			}
		},
		components:{
			swipeTab,
			commonList,
			loadmore
		},
		onLoad() {
			uni.getSystemInfo({
				success: res => {
					let height = res.windowHeight - uni.upx2px(400);
					this.swhegiht = height;
				}
			});
		}
	}
</script>

<style lang="scss" scoped>
.top{
	image{
		width: 100%;
		height: 500rpx;
	}
}
.tubiao{
	position: absolute;
	top: 60rpx;
	left: 30rpx;
	background-color: rgba(0, 0, 0, 0.4);
	border-radius: 50%;
	width: 50rpx;
	height: 50rpx;
	color: #FFFFFF;
	font-size: 34rpx;
}
.tubiao2{
	position: absolute;
	top: 60rpx;
	right: 30rpx;
	background-color: rgba(0, 0, 0, 0.4);
	border-radius: 50%;
	width: 50rpx;
	height: 50rpx;
	color: #FFFFFF;
	font-size: 34rpx;
}
.top_mid{
	flex-direction: row;
	position: absolute;
	top: 100rpx;
	left: 43%;
	.top_mida{
		image{
			border: 1rpx solid #FFFFFF;
			width: 130rpx;
			height: 130rpx;
			border-radius: 50%;
		}
	}
	.top_midb{
		text{
			color: #FFFFFF;
			font-size: 30rpx;
			margin-right: 10rpx;
		}
		view{
			width: 60rpx;
			height: 30rpx;
			border-radius: 20rpx;
			background-color: #007AFF;
			color: #FFFFFF;
			font-size: 22rpx;
			border: 1rpx solid #FFFFFF;
		}
		.viewact{
			width: 60rpx;
			height: 30rpx;
			border-radius: 20rpx;
			background-color: pink;
			color: #FFFFFF;
			font-size: 12rpx;
			border: 1rpx solid #FFFFFF;
		}
	}
	.top_midc{
		background-color: #FFE933;
		width: 120rpx;
		height: 50rpx;
		border-radius: 12rpx;
		font-size: 28rpx;
	}
}
.top_bom{
	position: absolute;
	top: 380rpx;
	background-color: #FFFFFF;
	width: 100%;
	color: #484848;
	height: 120rpx;
	font-weight: bold;
	justify-content:center;
	border-radius: 20rpx 20rpx 0 0;
	border-bottom: 20rpx solid #F4F4F4;
	view{
		text-align: center;
		width: 100rpx;
		margin: 0 auto;
	}
	.huise{
		color: #C1C1C1;
	}
}
.swiperbody{
	.item-1{
		width: 100%;
		view{
			width: 100%;
		}
		.item-1-1{
			padding: 20rpx;
			height: 180rpx;
			border-bottom: 1rpx solid #F2F2F2;
			.item-1-1-2{
				margin-top: 20rpx;
				color: #C1C1C1;
				font-size: 10rpx;
			}
		}
		.item-1-2{
			padding: 20rpx;
			width: 100%;
			height: 300rpx;
			border-bottom: 1rpx solid #F2F2F2;
			.item-1-1-2{
				margin-top: 20rpx;
				color: #C1C1C1;
				font-size: 10rpx;
			}
		}
		
	}
}
.top_show{
	padding: 20rpx;
	width: 400rpx;
	height: 200rpx;
	position: absolute;
	top: 100rpx;
	right: 30rpx;
	background-color: #FFFFFF;
	z-index: 1000;
	view{
		height: 100rpx;
		font-size: 30rpx;
	}
}
.paper-mask{
		position: fixed;
		right: 0;
		left: 0;
		top: 0;
		bottom: 0;
		z-index: 999;
	}
</style>
