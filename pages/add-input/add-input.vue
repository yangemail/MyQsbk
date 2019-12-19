<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="back" @clickLeft="back" @clickRight="submit">
			<view class="u-f-justify-align-center" style="flex: 1;" @tap="changelook">
				{{yinsi}}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
		<!-- 多行输入框 -->
		<view class="uni-textarea">
			<textarea v-model="text" placeholder="说一句话吧" />
			</view>		
		<!-- 上传多图 -->
		<uploadImage @upload="onUpload"></uploadImage>
		<!-- 弹出公告 -->
		<button class="button" type="primary" @click="togglePopup('center', 'popup')">中间弹出 popup</button>
		<uni-popup :show="showpopup" :type="type" @change="change">
			<view class="gonggao">
				<view class="u-f-justify-align-center">
					<image src="../../static/common/addinput.png" mode="widthFix"></image>
				</view>
				<view>1. 涉及黄色、政治、广告及骚扰信息</view>
				<view>2. 涉及黄色、政治、广告及骚扰信息</view>
				<view>3. 涉及黄色、政治、广告及骚扰信息</view>
				<view>4. 涉及黄色、政治、广告及骚扰信息</view>
				<button type="primary" @tap="change">朕知道了</button>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	let changelook = ["所有人可见", "仅自己可见"];
	
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue"
	import uploadImage from "../../components/common/upload-image.vue"
	import uniPopup from "../../components/uni-popup/uni-popup.vue"
	
	export default {
		components: {
			uniNavBar,
			uploadImage,
			uniPopup,
		},
		data() {
			return {
				showpopup: false,
				yinsi: "所有人可见",
				text:"",
				imgList: [],
				type: 'center',
				content: '弹 popup',
				isget: false,
			}
		},
		onBackPress() {
			console.log("onBackPress is pressed!")
			// 判断用户是否提交了信息：验证 text 和 imgList
			if(this.text || this.imgList.length>0) {
				if(!this.isget) {
					this.baocun();
					return true;
				}	
			}			
		},
		methods: {
			// 保存为草稿
			baocun() {
				uni.showModal({
					content:"是否要保存为草稿?", 
					cancelText:"不保存",
					confirmText:"保存",
					success: res => {
						if(res.confirm) {
							console.log("保存");
						} else {
							console.log("不保存");
						}
						this.isget = true;
						uni.navigateBack({
							delta: 1
						})
					}
				});
			},
			// 返回
			back() {
				uni.navigateBack({
					delta: 1
				})
			},
			// 发布
			submit() {
				console.log("发布")
			},
			// 隐私
			changelook() {
				console.log("隐私")
				uni.showActionSheet({ 
					itemList: changelook, // "itemList": 按钮的文字数组
					success: (res) => {
						console.log('选中了第' + (res.tapIndex + 1) + '个按钮');
						this.yinsi = changelook[res.tapIndex]
					},
				});
			},
			onUpload(arr) {
				this.imgList = arr;
				console.log(this.imgList)
			},
			// hidePopup() {
			// 	this.showpopup = false;
			// },
			togglePopup(type, open) {
				console.log('togglePopup() is called! ---');
				this.content = '居中弹出 popup'
				this.type = type
				this['show' + open] = true
			},
			change(e) {
				console.log('是否打开:' + e.show)
				if (!e.show) {
					this.showpopup = false
				}
			},
		}
	}
</script>

<style>
	.uni-textarea {
		border: 1upx solid #EEE;
	}
		
	.gonggao{
		width:500upx;
		/* #ifndef APP-NVUE */
		display: block; 
		/* #endif */
		background-color: #fff;
		padding: 15px;
		font-size: 14px;
		border-radius: 2%;
	}
	
	.gonggao image{
		width: 85%;
		border: none;
	}
	.gonggao button{
		margin-top: 20upx;
		background: #FFE934;
		color: #171606;
	}
</style>
