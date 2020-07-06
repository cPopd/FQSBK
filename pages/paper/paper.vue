<template>
	<view class="body">
		<!-- 小纸条列表 -->
		<papersLeftPopup :show="show" @hide="hidepopup" @addfriend="addfriend" @clear="clear"></papersLeftPopup>
		<papersList :datalist="datalist"></papersList>
		<loadmore :loadtext="loadtext"></loadmore>
	</view>
</template>

<script>
	import uniBadge from "../../components/uni-badge/uni-badge.vue";
	import papersList from "../../components/papers/papers-list.vue";
	import loadmore from "../../components/common/load-more.vue";
	import papersLeftPopup from "../../components/papers/paper-left-popup.vue";
	export default {
		data() {
			return {
				datalist:[{
					titlepic:"../../static/datapic/28.jpg",
					name:"昵称昵称",
					date:"10:20",
					desc:"详细内容",
					descnum:1
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"小呆瓜",
					date:"10:20",
					desc:"详细内容",
					descnum:99
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"昵称昵称",
					date:"10:20",
					desc:"详细内容",
					descnum:37
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"小男孩",
					date:"10:20",
					desc:"详细内容",
					descnum:0
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"昵称昵称",
					date:"10:20",
					desc:"详细内容",
					descnum:0
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"昵称昵称",
					date:"10:20",
					desc:"详细内容",
					descnum:0
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"昵称昵称",
					date:"10:20",
					desc:"详细内容",
					descnum:0
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"昵称昵称",
					date:"10:20",
					desc:"详细内容",
					descnum:0
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"昵称昵称",
					date:"10:20",
					desc:"详细内容",
					descnum:0
				},],
				loadtext:"上拉加载更多",
				show:false
			}
		},
		methods: {
			getdata(){
				var obj = [{
					titlepic:"../../static/datapic/28.jpg",
					name:"下拉刷新",
					date:"10:20",
					desc:"详细内容",
					descnum:1
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"下拉刷新",
					date:"10:20",
					desc:"详细内容",
					descnum:99
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"下拉刷新",
					date:"10:20",
					desc:"详细内容",
					descnum:37
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"下拉刷新",
					date:"10:20",
					desc:"详细内容",
					descnum:0
				},
				{
					titlepic:"../../static/datapic/28.jpg",
					name:"昵称昵称",
					date:"10:20",
					desc:"详细内容",
					descnum:0
				}]
				this.datalist = obj
				uni.stopPullDownRefresh()
			},
			getScrollDate(){
				if(this.loadtext !="上拉加载更多"){
					return
				}
				this.loadtext = "加载中"
				setTimeout(()=>{
					var obj = {
						titlepic:"../../static/datapic/28.jpg",
						name:"昵称昵称",
						date:"10:20",
						desc:"详细内容",
						descnum:0
					}
					this.datalist.push(obj)
					this.loadtext = "上拉加载更多"
				},1000)
			},
			addfriend(){
				console.log('加好友')
				setTimeout(()=>{
					this.hidepopup()
				},500)
			},
			clear(){
				console.log('清除缓存')
				setTimeout(()=>{
					this.hidepopup()
				},500)
			},
			hidepopup(){
				this.show = false
			},
			showpopup(){
				this.show = true
			}
		},
		components:{
			uniBadge,
			papersList,
			loadmore,
			papersLeftPopup
		},
		//监听下拉刷新
		onPullDownRefresh() {
			setTimeout(()=>{
				this.getdata()
			},1000)
		},
		onPageScroll() {
			this.getScrollDate()
		},
		onNavigationBarButtonTap(e) {
			if(e.index == 1){
				this.show=true
			}
			if(e.index == 0){
				uni.navigateTo({
					url:'../user-list/user-list'
				})
			}
		}
	}
</script>

<style lang="scss">
	.body{
		padding: 20rpx;
	}

</style>
