<template>
	<view class="uni-container">
		<!-- 轮播图 -->
		<uni-swiper-dot :info="info" :current="current" :mode="mode" :dots-styles="dotsStyles" field="content">
			<swiper class="swiper-box" @change="change" autoplay="true">
				<swiper-item v-for="(item, index) in info" :key="index">
					<view :class="item.colorClass" class="swiper-item">
						<image class="image" :src="item.url" mode="aspectFill" />
					</view>
				</swiper-item>
			</swiper>
		</uni-swiper-dot>
		<!-- 商品列表 -->
		<view class="row-box">
			<view v-for="item in list" :key="item.id" class="goods-item">
				<goods
				  :thumbnail="item.thumbnail"
				  :descript="item.descript"
				  :price="item.price"
				  :customer="item.customer"
				  @click="clickCard"
				  ></goods>
			</view>
		</view>
	</view>
</template>

<script>
	import uniSwiperDot from '@/components/uni-swiper-dot/uni-swiper-dot.vue'
	import goods from '@/pages/goods/goods.vue'
	
	export default {
		components: {
			uniSwiperDot,
			goods,
		},
		data() {
			return {
				// 轮播图参数
				info: [
					{
						colorClass: 'uni-bg-red',
						url: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg',
						content: '内容 A'
					},
					{
						colorClass: 'uni-bg-green',
						url: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg',
						content: '内容 B'
					},
					{
						colorClass: 'uni-bg-blue',
						url: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/cbd.jpg',
						content: '内容 C'
					}
				],
				dotStyle: [
					{
						backgroundColor: 'rgba(0, 0, 0, .3)',
						border: '1px rgba(0, 0, 0, .3) solid',
						color: '#fff',
						selectedBackgroundColor: 'rgba(0, 0, 0, .9)',
						selectedBorder: '1px rgba(0, 0, 0, .9) solid'
					},
					{
						backgroundColor: 'rgba(255, 90, 95,0.3)',
						border: '1px rgba(255, 90, 95,0.3) solid',
						color: '#fff',
						selectedBackgroundColor: 'rgba(255, 90, 95,0.9)',
						selectedBorder: '1px rgba(255, 90, 95,0.9) solid'
					},
					{
						backgroundColor: 'rgba(83, 200, 249,0.3)',
						border: '1px rgba(83, 200, 249,0.3) solid',
						color: '#fff',
						selectedBackgroundColor: 'rgba(83, 200, 249,0.9)',
						selectedBorder: '1px rgba(83, 200, 249,0.9) solid'
					}
				],
				modeIndex: -1,
				styleIndex: -1,
				current: 0,
				mode: 'default',
				dotsStyles: {},
				// 商品列表
				list: [
					{
						id: 0,
						thumbnail: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg',
						descript: '修冬季加绒大码套头卫衣套装难学生韩版宽松两件套男士休闲运动装&nbsp;黑色圆领加绒大三叶&nbsp;L',
						price: '2351',
						customer: '23',
					}, {
						id: 1,
						thumbnail: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg',
						descript: '这是一个基础卡片示例',
						price: '1864',
						customer: '50',
					}, {
						id: 2,
						thumbnail: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg',
						descript: '这是一个基础卡片示例，内容较少，此示例不带边框阴影。',
						price: '78.4',
						customer: '71',
					}, {
						id: 3,
						thumbnail: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg',
						descript: '这是一个基础卡片示例，内容较少，此示例不带边框阴影。',
						price: '47',
						customer: '185',
					},
				],
				
			}
		},
		methods: {
			clickCard(val) {
				console.log(val)
				uni.showModal({
					title: '点击卡片',
					content: val,
				})
			},
			// 轮播图事件
			change(e) {
				this.current = e.detail.current
			},
			selectStyle(index) {
				this.dotsStyles = this.dotStyle[index]
				this.styleIndex = index
			},
			selectMode(mode, index) {
				this.mode = mode
				this.modeIndex = index
				this.styleIndex = -1
				this.dotsStyles = this.dotStyle[0]
			}
		}
	}
</script>

<style>
	.uni-container {
		padding: 5rpx;
		background-color: #e9e9e9;
	}

	/* 轮播图样式 start */
	.swiper-box {
		height: 200px;
	}

	.swiper-item {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background-color: #999;
		color: #fff;
	}

	.image {
		width: 750rpx;
	}
	/* 轮播图样式 end */

	.row-box {
		/* padding: 5rpx 0; */
		padding-bottom: 0;

	}
	
	.row-box {
		/* display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center; */
		font-size: 14rpx;
		background-color: #e9e9e9;
		margin-top: 10rpx;
		
		column-count: 2;
		column-gap: 10rpx;
	}
	.goods-item {
		/* width: 50%; */
	}

</style>
