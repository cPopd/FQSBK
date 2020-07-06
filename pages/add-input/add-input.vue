<template>
	<view>
		<!-- 自定义导航栏 -->
		<uniNavBar :statusBar="true" rightText="发布" left-icon="back" @clickLeft="back" @clickRight="submit">
			<view class="tit u-f-ajc" @tap="changelook">
				{{ yins }}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uniNavBar>
		<!-- 多行富文本输入框 -->
		<view class="uni-textarea"><textarea v-model="text" placeholder="说一句话吧~" /></view>
		<!-- 上传多个图片 -->
		<view class="">
			<uploadImage @uploud="uoloud"></uploadImage>
		</view>
		
	</view>
</template>

<script>
let yinslist = ['所有人可见', '仅自己可见'];
import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue';
import uploadImage from '../../components/common/upload-image.vue';
export default {
	data() {
		return {
			yins: '所有人可见',
			text: '',
			imglist:[],
			isget:false
		};
	},
	methods: {
		//返回
		back() {
			uni.navigateBack({
				delta: 1
			});
		},
		//发布
		submit() {
			console.log('发布');
		},
		//改变状态
		changelook() {
			uni.showActionSheet({
				itemList: yinslist,
				success: res => {
					this.yins = yinslist[res.tapIndex];
				}
			});
		},
		uoloud(e){
			this.imglist = e;
		},
		baocun(){
			uni.showModal({
				content:'是否保存为草稿?',
				cancelText:'不保存',
				confirmText:'保存',
				success: (res) => {
					if(res.confirm){
						console.log('22')
					}else{
						console.log(123)
					}
					this.isget=true
					uni.navigateBack({
						delta:1
					});
				},
			});
		}
	},
	components: {
		uniNavBar,
		uploadImage
	},
	//监听页面返回
	onBackPress() {
		if(!this.text && this.imglist.length<1){return}
		if(!this.isget){
		this.baocun();
		return true
		}
	}
};
</script>

<style lang="scss">
.uni-textarea {
	border: 2rpx solid #eeeeee;
}
	.tit{
		margin: 0 auto;
	}
</style>
