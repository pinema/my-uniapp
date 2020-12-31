<template>
	<view>
		<view class="goods-area">
			<uni-nav-bar
			  left-icon="back" 
			  left-text="返回" 
			  right-text="菜单" 
			  title="导航栏组件"></uni-nav-bar>
			<view class="goods-list">
				<goodsList></goodsList>
			</view>
		</view>
		<view class="goods-carts">
			<uni-goods-nav
			  :fill="true"  
			  :options="options" 
			  :buttonGroup="buttonGroup"  
			  @click="onClick" 
			  @buttonClick="buttonClick" />
		</view>
	</view>
</template>

<script>
	import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue"
	import uniGoodsNav from '@/components/uni-goods-nav/uni-goods-nav.vue'
	import goodsList from '@/pages/goodsList/goodsList.vue'
	
	export default {
	    components: {
			uniNavBar,
			uniGoodsNav,
			goodsList,
		},
		data() {
			return {
				options: [
					{
						icon: 'headphones',
						text: '客服'
					}, {
						icon: 'shop',
						text: '店铺',
						info: 2,
						infoBackgroundColor:'#007aff',
						infoColor:"red"
					}, {
						icon: 'cart',
						text: '购物车',
						info: 2
					}],
					buttonGroup: [{
					  text: '加入购物车',
					  backgroundColor: '#ff0000',
					  color: '#fff'
					},
					{
					  text: '立即购买',
					  backgroundColor: '#ffa200',
					  color: '#fff'
					},
				],
				
			}
		},
		methods: {
			onClick (e) {
				uni.showToast({
				  title: `点击${e.content.text}`,
				  icon: 'none'
				})
			  },
			 buttonClick (e) {
				console.log(e)
				this.options[2].info++
			},
		}
	}
</script>

<style>
	.goods-area {
		position: fixed;
		height: 100%;
	}
	.goods-list {
		height: calc(100% - 50px - 44.5px);
		overflow: auto;
	}
	.goods-carts {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: column;
		position: fixed;
		left: 0;
		right: 0;
		bottom: 0;
	}
</style>
