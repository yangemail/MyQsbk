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
	/* #ifndef APP-PLUS-NVUE */
	/* uni.css - 通用组件、模板样式库，可以当作一套ui库应用 */
	/* 引入官方图标库 */
	@import './common/uni.css';
	/* 引入自定义图标库 */
	@import './common/icon.css';
	/* 引入自定义动画库 */
	@import './common/animate.css';
	/* 引入自定义公共样式 */
	@import url("./common/common.css");
	/* #endif*/
</style>
