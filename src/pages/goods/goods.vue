<template>
	<view>
		<view class="goods-box_item" @click="clickGoods">
			<!-- 商品图片 -->
			<view class="image-box">
				<image class="image" mode="aspectFill" :src="thumbnail" />
			</view>
			<!-- 商品描述 -->
			<view class="goods-descript">
				<text>{{descript}}</text>
			</view>
			<!-- 商品标签 -->
			<view></view>
			<!-- 商品价格 -->
			<view class="goods-info">
				<view class="goods-price"><text class="goods-price__item">¥{{parsePrice(price)}}</text></view>
				<view class="goods-customer"><text class="goods-customer__item">{{customer}}人付款</text></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'goods',
		props: {
			// 图片url
			thumbnail: {
				type: String,
				default: 'https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/shuijiao.jpg'
			},
			// 商品描述
			descript: {
				type: String,
				default: '修冬季加绒大码套头卫衣套装难学生韩版宽松两件套男士休闲运动装&nbsp;黑色圆领加绒大三叶&nbsp;L'
			},
			// 价格
			price: {
				type: String,
				default: '0'
			},
			// 付款人数
			customer: {
				type: String,
				default: '0'
			},
			// 商品标签
			goodsTags: {
				type: String,
				default: '',
			},
		},
		data() {
			return {

			}
		},
		methods: {
			// 价格格式转换
			parsePrice(val) {
			  if (!val) return 0.0
			  let USPrice = Number.parseFloat(val).toLocaleString('en-US')

			  let lastDot = USPrice.toString().indexOf('.')

			  return USPrice
			},
			// 商品点击事件
			clickGoods() {
				this.$emit('click', this.descript);
			},
		}
	}
</script>

<style>
	.goods-box_item {
		background-color: #ffffff;
		border: 1rpx solid #e9e9e9;
		border-radius: 10rpx;
		/* margin: 5rpx; */
	}

	.image-box {
		/* #ifndef APP-NVUE */
		display: flex;
		flex-direction: column;
		/* #endif */
		height: 350rpx;
		overflow: hidden;
	}

	.image {
		/* #ifndef APP-NVUE */
		width: 100%;
		height: 100%;
		/* #endif */
		flex: 1;
		border-radius: 10rpx 10rpx 0 0;
	}

	.goods-descript{
		font-size: 28rpx;
		/* line-height: 1.8; */
		padding: 0 15rpx;
		/* 显示两行描述 */
		/* height: 70rpx; */
		overflow: hidden;
		text-overflow: ellipsis;
		display: -webkit-box;
		-webkit-line-clamp: 2;
		-webkit-box-orient: vertical;
	}

	.goods-info {
		padding: 30rpx 15rpx 0 15rpx;
		padding-top: 30rpx;
		display: flex;
		align-items: center;
	}
	.goods-price__item {
		font-size: 36rpx;
		color: #FF0000;
	}
	.goods-customer {
		padding-left: 15rpx;
	}
	.goods-customer__item {
		font-size: 24rpx;
		color: #a7a7a7;
	}
</style>
