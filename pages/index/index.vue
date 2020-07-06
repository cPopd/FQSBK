<template>
	<view>
		<view>
			<!-- 上方导航 -->
			<swipeTab
			 :tabBars="tabBars" 
			 :tabIndex="tabIndex"
			 @tabtap="tabtap"
			 >
			 </swipeTab>
			<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swhegiht+'px'}" :current="tabIndex" @change="changeindex">
				<swiper-item v-for="(items,i) in newList.list" :key="i">
					
					<scroll-view scroll-y class="list" @scrolltolower="loadmore(i)">
						<template v-if="items.list.length>0">
							<!-- 图文列表 -->
							<block v-for="(item,index) in items.list" :key="index">
								<indexList :item="item" :index="index"></indexList>
							</block> 
							<!-- 上拉加载 -->
							<loadmore :loadtext="items.loadtext"></loadmore>
						</template>
						<template v-else>
							<!-- 无内容 -->
							<nothing></nothing>
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
			</view>
			
		</view>
	</view>
</template>

<script>
	import indexList from "../../components/index-list/index-list.vue";
	import swipeTab from "../../components/index-list/swipe-tab.vue";
	import loadmore from "../../components/common/load-more.vue";
	import nothing from "../../components/common/no-thing.vue";
export default {
	data() {
		return {
			swhegiht:500,
			tabBars:[
				{ name : "关注", id:"0" },
				{ name : "热点", id:"1" },
				{ name : "娱乐", id:"2" },
				{ name : "财经", id:"3" },
				{ name : "游戏", id:"4" },
				{ name : "体育", id:"5" },
				{ name : "新闻", id:"6" },
			],
			newList:{
				list:[
				{
					loadtext:"上拉加载更多",
					list:[{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: true,
					title: '我是标题',
					type: 'img',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11,
						index: 1 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				},
				{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: false,
					title: '我是标题',
					type: 'video',
					playnum: '20W',
					long: '2:35',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11, 
						index: 0 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				}]},
				{
					loadtext:'上拉加载更多',
					list:[]
				},
				{
					loadtext:'上拉加载更多',
					list:[
						{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: true,
					title: '我是标题',
					type: 'img',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11,
						index: 1 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				},
				{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: false,
					title: '我是标题',
					type: 'video',
					playnum: '20W',
					long: '2:35',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11, 
						index: 0 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				}]
				},
				{
					loadtext:'上拉加载更多',
					list:[{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: true,
					title: '我是标题',
					type: 'img',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11,
						index: 1 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				},
				{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: false,
					title: '我是标题',
					type: 'video',
					playnum: '20W',
					long: '2:35',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11, 
						index: 0 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				}]
				},
				{
					loadtext:'上拉加载更多',
					list:[{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: true,
					title: '我是标题',
					type: 'img',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11,
						index: 1 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				},
				{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: false,
					title: '我是标题',
					type: 'video',
					playnum: '20W',
					long: '2:35',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11, 
						index: 0 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				}]
				},
				{
					loadtext:'上拉加载更多',
					list:[{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: true,
					title: '我是标题',
					type: 'img',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11,
						index: 1 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				},
				{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: false,
					title: '我是标题',
					type: 'video',
					playnum: '20W',
					long: '2:35',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11, 
						index: 0 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				}]
				},
				{
					loadtext:'上拉加载更多',
					list:[{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: true,
					title: '我是标题',
					type: 'img',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11,
						index: 1 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				},
				{
					userpic: '../../static/userpic/12.jpg',
					username: '二狗不叫二狗',
					isguanzhu: false,
					title: '我是标题',
					type: 'video',
					playnum: '20W',
					long: '2:35',
					titlepic: '../../static/datapic/11.jpg',
					infonum: {
						dingnum: 11,
						cainum: 11, 
						index: 0 //0代表没被操作 1定了 2 踩了
					},
					commentnum: 10,
					sharenum: 10
				}]
				}
			]
			},
			tabIndex:0
		};
	},
	onLoad() {
		uni.getSystemInfo({
			success: (res) => {
				let height = res.windowHeight - uni.upx2px(100)
				this.swhegiht = height
			}
		})
	},
	//监听原生搜索框
	onNavigationBarSearchInputClicked() {
		uni.navigateTo({
			url:'../search/search'
		})
	},
	onNavigationBarButtonTap(e) {
		if(e.index == 1){
			uni.navigateTo({
				url:'../add-input/add-input'
			})
		}
	},
	methods: {
		/* 点击改变视图 */
		tabtap(e){
			this.tabIndex = e
		},
		/* 滑动改变视图 */
		changeindex(e){
			this.tabIndex = e.detail.current
		},
		/* 上拉加载 */
		loadmore(e){
			if(this.newList.list[e].loadtext!="上拉加载更多"){
				return;
			}
			//修改装填
			this.newList.list[e].loadtext = "加载中.....";
			//获取数据
			setTimeout(()=>{
				//获取完成
				var obj = {
						userpic: '../../static/userpic/12.jpg',
						username: '二狗不叫二狗',
						isguanzhu: false,
						title: '我是标题',
						type: 'video',
						playnum: '20W',
						long: '2:35',
						titlepic: '../../static/datapic/11.jpg',
						infonum: {
							dingnum: 11,
							cainum: 11, 
							index: 0 //0代表没被操作 1定了 2 踩了
						},
						commentnum: 10,
						sharenum: 10
				}
				this.newList.list[e].list.push(obj)
				this.newList.list[e].loadtext = "上拉加载更多";
			},500)
			
			//his.newList.list[e].loadtext = "没有更多数据";
		}
	},
	components:{
		indexList,
		swipeTab,
		loadmore,
		nothing
	}
};
</script>

<style lang="scss">

</style>
