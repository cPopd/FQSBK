<template>
	<view>
		<swipeTab :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swipeTab>

		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{ height: swhegiht + 'px' }" :current="tabIndex" @change="changeindex">
				<swiper-item v-for="(items, i) in newList.list" :key="i">
					<scroll-view scroll-y class="list" @scrolltolower="loadmore(i)">
						<template v-if="items.list.length > 0">
							<!-- 话题列表 -->
							<!-- <block v-for="(item, index) in items.list" :key="index"> -->
								<topList :list="newList.list[i].list"></topList>
								<!-- </block> -->
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
</template>

<script>
import swipeTab from '../../components/index-list/swipe-tab.vue';
import nothing from '../../components/common/no-thing.vue';
import loadmore from '../../components/common/load-more.vue';
import topList from '../../components/new-tab/top-list';
export default {
	data() {
		return {
			tabBars: [
				{ name: '关注', id: '0' },
				{ name: '热点', id: '1' },
				{ name: '娱乐', id: '2' },
				{ name: '财经', id: '3' },
				{ name: '游戏', id: '4' },
				{ name: '体育', id: '5' },
				{ name: '新闻', id: '6' }
			],
			tabIndex: 0,
			swhegiht: 500,
			newList: {
				list: [
					{
						loadtext: '上拉加载更多',
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
						},{
							titlepic:'../../static/demo66.jpg',
							title:"话题名称",
							desc:"话题描述内容",
							totalnum:50,
							todaynum:10
						},{
							titlepic:'../../static/demo66.jpg',
							title:"话题名称",
							desc:"话题描述内容",
							totalnum:50,
							todaynum:10
						},{
							titlepic:'../../static/demo66.jpg',
							title:"话题名称",
							desc:"话题描述内容",
							totalnum:50,
							todaynum:10
						},{
							titlepic:'../../static/demo66.jpg',
							title:"话题名称",
							desc:"话题描述内容",
							totalnum:50,
							todaynum:10
						}
					],
					},
					{
						loadtext: '上拉加载更多',
						list: [
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
					]
					},
					{
						loadtext: '上拉加载更多',
						list: [
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
					]
					},
					{
						loadtext: '上拉加载更多',
						list: [
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
					]
					},
					{
						loadtext: '上拉加载更多',
						list: []
					},
					{
						loadtext: '上拉加载更多',
						list: [
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
					]
					},
					{
						loadtext: '上拉加载更多',
						list: [
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
					]
					}
				]
			},
		};
	},
	methods: {
		/* 点击改变视图 */
		tabtap(e) {
			this.tabIndex = e;
		},
		/* 滑动改变视图 */
		changeindex(e) {
			this.tabIndex = e.detail.current;
		},
		/* 上拉加载 */
		loadmore(e) {
			if (this.newList.list[e].loadtext != '上拉加载更多') {
				return;
			}
			//修改装填
			this.newList.list[e].loadtext = '加载中.....';
			//获取数据
			setTimeout(() => {
				var obj = {
					titlepic:'../../static/demo66.jpg',
					title:"话题名称",
					desc:"话题描述内容",
					totalnum:50,
					todaynum:10
				}
				this.newList.list[e].list.push(obj)
				//获取完成
				this.newList.list[e].loadtext = '上拉加载更多';
			}, 500);

			//his.newList.list[e].loadtext = "没有更多数据";
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
		swipeTab,
		nothing,
		loadmore,
		topList
	}
};
</script>

<style></style>
