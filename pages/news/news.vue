<template>
	<view>
		<!-- 自定义导航栏 -->
		<newsNavBar :tabBars="tabBars" :tabIndex="tabIndex" @change-tab="change"></newsNavBar>
		<!-- 列表 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{ height: swhegiht + 'px' }" :current="tabIndex" @change="changeindex">
				<!-- 关注 -->
				<swiper-item>
					<scroll-view scroll-y class="list" @scrolltolower="loadmore">
						<block v-for="(item, index) in list.list" :key="index">
						<common-list :item="item" :index="index" ></common-list>
						</block>
						<!-- 上拉加载 -->
						<loadmore :loadtext="list.loadtext"></loadmore>
					</scroll-view>
				</swiper-item>
				<!-- 话题 -->
				<swiper-item>
					<scroll-view scroll-y class="list">
				<!-- 搜索框 -->
				<view class="search-input">
					<input class="uni-input" 
					placeholder-class="icon iconfont icon-sousuo topic-search" 
					placeholder="搜索内容" />
				</view>
				<!-- 轮播图 -->
				<swiper :indicator-dots="true" :autoplay="true" 
				:interval="3000" :duration="1000" class="top-swiper">
				<block v-for="(date,dateindex) in topic[0].swiper" :key="dateindex">
					<swiper-item>
						<image :src="date.src" mode="widthFix" lazy-load>
						</image>
					</swiper-item>
				</block>
				</swiper>
				<!-- 热门分类 -->
				<topNav :fenlei="topic[0].fenlei"></topNav>
				<!-- 最近更新 -->
				<topList :list="topic[0].list"></topList>
				</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
import commonList from '../../components/common/common-list.vue';
import newsNavBar from '../../components/new-tab/news-nav-bar.vue';
import loadmore from '../../components/common/load-more.vue';
import topNav from '../../components/new-tab/top-nav';
import topList from '../../components/new-tab/top-list';
export default {
	data() {
		return {
			tabIndex: 0,
			swhegiht: 500,
			topic:[{
				swiper:[
					{
						src:"../../static/datapic/22.jpg"
					},
					{
						src:"../../static/datapic/22.jpg"
					},
					{
						src:"../../static/datapic/22.jpg"
					}
				],
				fenlei:[
					{
						name:'最新'
					},
					{
						name:'游戏'
					},{
						name:'打卡'
					},{
						name:'情感'
					},{
						name:'故事'
					},{
						name:'喜爱'
					}
				],
				list:[
					{
						titlepic:'../../static/demo66.jpg',
						title:"话题名称",
						desc:"话题描述内容",
						totalnum:50,
						todaynum:10
					},
					{
						titlepic:'../../static/demo66.jpg',
						title:"话题名称",
						desc:"话题描述内容",
						totalnum:50,
						todaynum:10
					},
					{
						titlepic:'../../static/demo66.jpg',
						title:"话题名称",
						desc:"话题描述内容",
						totalnum:50,
						todaynum:10
					},
					{
						titlepic:'../../static/demo66.jpg',
						title:"话题名称",
						desc:"话题描述内容",
						totalnum:50,
						todaynum:10
					}
				],
				}
			],
			tabBars: [{ name: '关注', id: 'guanzhu' }, { name: '话题', id: 'huati' }],
			list: {
				loadtext: '上拉加载更多',
				list: [
					// 文字
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 1, //0 男 1 女
						age: 25,
						isguanzhu: false,
						title: '我是标题',
						titlepic: '',
						video: false,
						share: false,
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					// 图文
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 0, //0 男 1 女
						age: 25,
						isguanzhu: false,
						title: '我是标题',
						titlepic: '../../static/datapic/21.jpg',
						video: false,
						share: false,
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					// 视频
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 0, //0 男 1 女
						age: 25,
						isguanzhu: false,
						title: '我是标题',
						titlepic: '../../static/datapic/21.jpg',
						video: {
							looknum: '20w',
							long: '2:47'
						},
						share: false,
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					},
					// 分享
					{
						userpic: '../../static/demo7.jpg',
						username: '哈哈',
						sex: 0, //0 男 1 女
						age: 25,
						isguanzhu: false,
						title: '我是标题',
						titlepic: '',
						video: false,
						share: {
							title: '我是分享的标题',
							titlepic: '../../static/userpic/14.jpg'
						},
						path: '深圳 龙岗',
						sharenum: 20,
						commentnum: 30,
						goodnum: 20
					}
				]
			}
		};
	},
	methods: {
		//点击切换
		change(index) {
			this.tabIndex = index;
		},
		//滑动切换
		changeindex(e) {
			this.tabIndex = e.detail.current;
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
						sex: 0, //0 男 1 女
						age: 25,
						isguanzhu: false,
						title: '我是标题',
						titlepic: '../../static/datapic/21.jpg',
						video: {
							looknum: '20w',
							long: '2:47'
						},
						}
				this.list.list.push(obj)
				//获取完成
				this.list.loadtext = "上拉加载更多";
			},500)
			//this.newList[e].loadtext = "没有更多数据";
		}
	},
	onLoad() {
		uni.getSystemInfo({
			success: res => {
				let height = res.windowHeight - uni.upx2px(100);
				this.swhegiht = height;
			}
		});
	},
	components: {
		commonList,
		newsNavBar,
		loadmore,
		topNav,
		topList
	}
};
</script>

<style lang="scss">
	.top-swiper{
		padding: 0 20rpx 20rpx 20rpx;
		image{
			width: 100%;
			border-radius: 20rpx;
		}
	}
	.search-input{
		padding: 20rpx;
		input{
			background-color: #F4F4F4;
			border-radius: 10rpx;
		}
	}
	.topic-search{
		display: flex;
		justify-content: center;
		font-size: 28rpx;
	}

</style>
