<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>
 
<style>
	/*每个页面公共css */
	@import './common/uni.css';/* 官方css库 */
	@import './common/animate.css';/* 动画库 */
	@import './common/icon.css';/* 阿里图标库 */
	@import './common/flex.css';/* 封装flex布局 */
</style>
