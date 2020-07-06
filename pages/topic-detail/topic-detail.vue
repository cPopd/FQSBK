<template>
	<view>
		<!-- 话题介绍 -->
		<topicDetail :item="topinfo"></topicDetail>
		<!-- tab切换 -->
		<swipeTab
		 :tabBars="tabBars" 
		 :tabIndex="tabIndex"
		 @tabtap="tabtap"
		 :scrollStrle="scrollStrle"
		 :scrollItemStrle="scrollItemStrle"
		 >
		 </swipeTab>
		 <!-- 列表-->
		 <view class="topic-detail-list">
			 <block v-for="(item,index) in tablist" :key="index">
				 <template v-if="tabIndex == index">
					 <!-- 列表-->
					 <block v-for="(items,i) in item.list" :key="i">
						 <common-list :item="items" :index="i" ></common-list>
					 </block>
					 <!-- 上拉加载-->
					 <loadmore :loadtext="item.loadtext"></loadmore>
				 </template>
			 </block>
		 </view>
	</view>
</template>

<script>
	import topicDetail from "../../components/topic/topic-detail.vue"; 
	import swipeTab from "../../components/index-list/swipe-tab.vue";
	import commonList from '../../components/common/common-list.vue';
	import loadmore from '../../components/common/load-more.vue';
	export default {
		data() {
			return {
				topinfo:{
					titlepic:"../../static/datapic/36.jpg",
					titile:"标题标题",
					desc:"描述描述",
					totalnum:"200",
					todaynum:"300"
				},
				tabIndex:0,
				tabBars:[
					{name:'默认',id:'moren'},
					{name:'最新',id:'zuixin'}
				],
				scrollStrle:'border-bottom: 0',
				scrollItemStrle:'width: 50%',
				tablist:[{
					loadtext:"上拉加载更多",
					list:[
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
				},
				{
						loadtext:"上拉加载更多",
						list:[
								// 文字
								{
									userpic: '../../static/demo7.jpg',
									username: '哈哈哈哈哈哈哈啊',
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
					
				}]
			}
		},
		methods: {
			//上拉刷新
			getdata(){
				//获取数据
				let arr = [{
						userpic: '../../static/demo7.jpg',
						username: '下拉刷新测试',
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
				{
						userpic: '../../static/demo7.jpg',
						username: '下拉刷新测试',
						sex: 0, //0 男 1 女
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
				},]
				//赋值
				this.tablist[this.tabIndex].list=arr;
				//关闭下拉刷新
				uni.stopPullDownRefresh()
			},
			tabtap(e){
				this.tabIndex = e
			},
			loadmore(){
				if(this.tablist[this.tabIndex].loadtext!="上拉加载更多"){
					return;
				}
				//修改装填
				this.tablist[this.tabIndex].loadtext = "加载中.....";
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
					this.tablist[this.tabIndex].list.push(obj)
					//获取完成
					this.tablist[this.tabIndex].loadtext = "上拉加载更多";
				},500)
				//this.newList[e].loadtext = "没有更多数据";
			}
		},
		components:{
			topicDetail,
			swipeTab,
			commonList,
			loadmore
		},
		/* 页面触底 */
		onReachBottom(){
			this.loadmore();
		},
		/* 下拉刷新 */
		onPullDownRefresh() {
			setTimeout(()=>{
				this.getdata()
			},1000)
			
		}
	}
</script>

<style lang="scss">
</style>
