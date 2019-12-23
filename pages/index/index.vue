<template>
	<view>

		<swiperTabHead :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swiperTabHead>

		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height: swiperheight+'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(items, index1) in newslist" :key="index1">
					<scroll-view scroll-y class="list" @scrolltolower="loadmore(index1)">
						
						<template v-if="items.list.length>0">
							<!-- 图文列表 -->
							<block v-for="(item, index2) in items.list" :key="index2">
								<indexList :item="item" :index="index2"></indexList>
							</block>
							<!-- 上拉加载 -->
							<loadMore :loadtext="items.loadtext"></loadMore>
						</template>
						<template v-else>
							<!-- 无内容 -->
							<nothing/>
						</template>
						
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import swiperTabHead from '../../components/index/swiper-tab-head.vue';
	import indexList from '../../components/index/index-list.vue';
	import loadMore from '../../components/common/load-more.vue';
	import nothing from '../../components/common/no-thing.vue';

	export default {
		components: {
			indexList,
			swiperTabHead,
			loadMore,
			nothing,
		},
		data() {
			return {
				swiperheight: 700,
				tabIndex: 0,
				tabBars: [{
						name: "关注",
						id: "guanzhu"
					},
					{
						name: "推荐",
						id: "tuijian"
					},
					{
						name: "体育",
						id: "tiyu"
					},
					{
						name: "热点",
						id: "redian"
					},
					{
						name: "财经",
						id: "caijing"
					},
					{
						name: "娱乐",
						id: "yule"
					},
				],

				newslist: [{
						loadtext: "上拉加载更多",
						list: [{
							userpic: "../../static/demo/userpic/12.jpg",
							username: "昵称",
							isguanzhu: false,
							title: "我是标题",
							type: "img", // img: 图文, video: 视频
							titlepic: "../../static/demo/datapic/11.jpg",
							infonum: {
								index: 0, // 0. 没有操作；1. 顶过了；2. 踩过了
								dingnum: 11,
								cainum: 11,
							},
							commentnum: 10,
							sharenum: 10,
						}, {
							userpic: "../../static/demo/userpic/12.jpg",
							username: "昵称",
							isguanzhu: true,
							title: "我是标题",
							type: "video", // img: 图文, video: 视频
							titlepic: "../../static/demo/datapic/11.jpg",
							playnum: "20w",
							long: "2:47",
							infonum: {
								index: 1, // 0. 没有操作；1. 顶过了；2. 踩过了
								dingnum: 11,
								cainum: 11,
							},
							commentnum: 10,
							sharenum: 10,
						}]
					},
					{
						loadtext: "上拉加载更多",
						list: [{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}, {
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}, {
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}
						]
					},
					{
						loadtext: "上拉加载更多",
						list: [{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}, {
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}, {
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							},
							{
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: false,
								title: "我是标题",
								type: "img", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								infonum: {
									index: 0, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}, {
								userpic: "../../static/demo/userpic/12.jpg",
								username: "昵称",
								isguanzhu: true,
								title: "我是标题",
								type: "video", // img: 图文, video: 视频
								titlepic: "../../static/demo/datapic/11.jpg",
								playnum: "20w",
								long: "2:47",
								infonum: {
									index: 1, // 0. 没有操作；1. 顶过了；2. 踩过了
									dingnum: 11,
									cainum: 11,
								},
								commentnum: 10,
								sharenum: 10,
							}
						]
					},
					{
						loadtext: "上拉加载更多",
						list: []
					},
					{
						loadtext: "上拉加载更多",
						list: []
					},
					{
						loadtext: "上拉加载更多",
						list: []
					},
				],
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					let height = res.windowHeight - uni.upx2px(100);
					console.log(height);
					this.swiperheight = height;
				}
			});
		},
		// 监听搜索框点击事件
		onNavigationBarSearchInputClicked() {
			uni.navigateTo({
				url:"../search/search",
			})
		},
		// 监听原生标题导航按钮点击事件
		onNavigationBarButtonTap(e) {
			console.log("Called onNavigationBarButtonTap(e) >> " + e.index)
			switch(e.index) {
				// 打开发布页面
				case 1:
					uni.navigateTo({
						url:"../add-input/add-input"
					})
					break;
			}
			
		},
		methods: {
			// tabbar点击事件
			tabtap(index) {
				console.log("$$$tabtap(index) -> " + index);
				this.tabIndex = index;
			},
			// swiper滑动事件
			tabChange(e) {
				// tabChange为事件，随着tab的改变而改变。e.detail>>0, touch; e.detail>>1, touch
				console.log("e.detail >>> " + e.detail.current + "," + e.detail.source)
				this.tabIndex = e.detail.current;
			},
			// 上拉加载事件
			loadmore(index) {
				if (this.newslist[index].loadtext != "上拉加载更多") {
					return;
				}
				// 修改状态
				this.newslist[index].loadtext = "加载中...";
				// 获取数据
				setTimeout(() => {
					// 获取完成
					let obj = {
						userpic: "../../static/demo/userpic/12.jpg",
						username: "昵称（最新的）",
						isguanzhu: true,
						title: "我是标题（最新的）",
						type: "video", // img: 图文, video: 视频
						titlepic: "../../static/demo/datapic/11.jpg",
						playnum: "20w",
						long: "2:47",
						infonum: {
							index: 1, // 0. 没有操作；1. 顶过了；2. 踩过了
							dingnum: 11,
							cainum: 11,
						},
						commentnum: 10,
						sharenum: 10,
					};
					this.newslist[index].list.push(obj);
					this.newslist[index].loadtext = "上拉加载更多";
				}, 1000);
				this.newslist[index].loadtext = "没有更多数据了 - 666测试数据";
			},
		}
	}
</script>

<style>

</style>
