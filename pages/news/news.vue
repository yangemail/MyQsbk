<template>
	<view>
		<!-- 自定义导航栏 -->
		<uniNavBar :statusBar="true" @clickRight="openAdd">
			<!-- 左边 -->
			<block slot="left">
				<view class="nav-left">
					<view class="icon iconfont icon-qiandao"></view>
				</view>
			</block>
			<!-- 中间 -->
			<view class="nav-tab-bar u-f-justify-align-center">
				<block v-for="(tab, index) in tabBars" :key="tab.id">
					<view class="u-f-justify-align-center" :class="{'active':(tabIndex==index)}" @tap="changeTab(index)">
						{{tab.name}}
						<view class="nav-tab-bar-line" v-if="(tabIndex==index)"></view>
					</view>
				</block>
			</view>
			<!-- 右边 -->
			<block slot="right">
				<view class="nav-right u-f-justify-align-center">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</block>
		</uniNavBar>
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue";

	export default {
		components: {
			uniNavBar,
		},
		data() {
			return {
				tabIndex: 0,
				tabBars: [
					{name:"关注",id:"guanzhu"},
					{name:"话题",id:"topic"},
				]
			}
		},
		methods: {
			openAdd() {
				// 打开发布页面
				uni.navigateTo({
					url: '../add-input/add-input',
				});
			},
			changeTab(index) {
				console.log("changeTab(index) >> " + index);
				this.tabIndex = index;
			},
		},
	}
</script>

<style>
	.nav-left>view,
	.nav-right>view {
		font-size: 40upx;
	}
	
	.nav-left>view{
		color: #FF9619;
	}

	.nav-left {
		margin-left: 16upx;
	}

	.nav-right {
		width: 100%;
	}
	
	.nav-tab-bar{
		width: 100%;
		margin-left: -20upx;
	}
	
	.nav-tab-bar>view{
		font-size: 32upx;
		padding: 0 15upx;
		font-weight: bold;
		color: #969696;
		position: relative;
	}
	
	.active {
		color: #333!important;
	}
	
	.nav-tab-bar-line {
		border-bottom: 5upx solid #FEDE33;
		border-top: 5upx solid #FEDE33;
		width: 70upx;
		border-radius: 20upx;
		position: absolute;
		bottom: 0upx;
	}
</style>
