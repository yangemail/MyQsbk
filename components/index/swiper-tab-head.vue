<template>
	<!-- 顶部滚动条 -->
	<view class="uni-tab-bar">
		<scroll-view scroll-x class="uni-swiper-tab">
			<block v-for="(tab, index) in tabBars" :key="tab.id">
				<view class="swiper-tab-list" :class="{active:(index==tabIndex)}" @tap="tabtap(index)">
					{{tab.name}}
					<view class="swiper-tab-line"></view>
				</view>
			</block>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props: {
			tabBars: Array,
			tabIndex: Number
		},
		data() {
			return {
				
			}
		},
		methods: {
			// tabbar点击事件
			tabtap(index) {
				// this.tabIndex = index;
				this.$emit('tabtap', index); // 子组件传值给父组件
			},
		},
	}
</script>

<style scoped>
	.uni-swiper-tab {
		border-bottom: 1upx solid #EEE;
	}

	.swiper-tab-list {
		color: #969696;
		font-weight: bold;
	}

	.uni-tab-bar .active {
		color: #343434;
	}

	.active .swiper-tab-line {
		border-top: 6upx solid #FEDE33;
		border-bottom: 6upx solid #FEDE33;
		border-radius: 20upx;
		width: 70upx;
		margin: auto;
	}
</style>
