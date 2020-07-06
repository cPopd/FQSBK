<template>
	<view class="body">
		<!-- tab切换 -->
		<swipeTab
		 :tabBars="tabBars" 
		 :tabIndex="tabIndex"
		 @tabtap="tabtap"
		 :scrollStrle="scrollStrle"
		 :scrollItemStrle="scrollItemStrle"
		 >
		 </swipeTab>
		 
		 <swiper class="swiper-box" :style="{height:swhegiht+'px'}" :current="tabIndex" @change="changeindex">
		 	<swiper-item v-for="(items,i) in newList" :key="i">
		 		<scroll-view scroll-y class="list" @scrolltolower="loadmore(i)">
		 			<template v-if="items.list.length>0">
		 			<!-- 好友列表-->
		 				<block v-for="(item,index) in items.list" :key="index">
		 					<userList :item="item" :index="index"></userList> 
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
</template>

<script>
	import swipeTab from "../../components/index-list/swipe-tab.vue";
	import userList from "../../components/user-list/user-list.vue";
	import loadmore from "../../components/common/load-more.vue";
	export default {
		data() {
			return {
				tabIndex:0,
				swhegiht:500,
				tabBars:[
					{name:'互关',id:'huguan',num:10},
					{name:'关注',id:'guanzhu',num:20},
					{name:'粉丝',id:'fensi',num:30}
				],
				scrollStrle:'border-bottom:0',
				scrollItemStrle:'width:33%',
				newList:[
					{
						loadtext:"上拉加载更多",
						list:[{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗",
							sex:1,
							age:20,
							isguanzhu:true
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						},]
					},
					{
						loadtext:"上拉加载更多",
						list:[{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗",
							sex:1,
							age:20,
							isguanzhu:true
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						}]
					},
					{
						loadtext:"上拉加载更多",
						list:[{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗",
							sex:1,
							age:20,
							isguanzhu:true
						},
						{
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						}]
					}
				]
			}
		},
		methods: {
			tabtap(e){
				this.tabIndex = e
			},
			changeindex(e){
				this.tabIndex = e.detail.current
			},
			/* 上拉加载 */
			loadmore(e){
				if(this.newList[e].loadtext!="上拉加载更多"){
					return;
				}
				//修改装填
				this.newList[e].loadtext = "加载中.....";
				//获取数据
				setTimeout(()=>{
					//获取完成
					var obj = {
							userpic:"../../static/datapic/11.jpg",
							username:"二狗不叫二狗2",
							sex:0,
							age:20,
							isguanzhu:false
						}
					this.newList[e].list.push(obj)
					this.newList[e].loadtext = "上拉加载更多";
				},500)
				
				//his.newList.list[e].loadtext = "没有更多数据";
			}
		},
		components:{
			swipeTab,
			userList,
			loadmore
		},
		//监听导航按钮事件
		onNavigationBarButtonTap(e) {
			if(e.index == 0){
				uni.navigateBack({
					delta:1
				})
			}
		},
		onLoad() {
			console.log(this.newList[1].list)
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(100)
					this.swhegiht = height
				}
			})
		}
	}
</script>

<style lang="scss">
	.body{
		padding: 0 20rpx;
	}

</style>
