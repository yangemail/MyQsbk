<template>
	<view>
		搜索页
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		// 监听原生标题的导航按钮点击事件
		onNavigationBarButtonTap(e) {
			console.log(JSON.stringify(e))
			if (e.index == 0) {
				uni.navigateBack({
					delta: 1
				})
			}
		},
		// 监听搜索框文本变化
		onNavigationBarSearchInputChanged(e) {
			// console.log("监听搜索框文本变化"+JSON.stringify(e));
			console.log(e.text);
		},
		// 监听点击输入法键盘搜索按钮事件
		onNavigationBarSearchInputConfirmed(e) {
			// console.log("监听点击输入法键盘搜索按钮事件"+JSON.stringify(e));
			console.log(e.text);
		},
		methods: {

		}
	}
</script>

<style>

</style>
