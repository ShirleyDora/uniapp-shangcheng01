<template>
	<view>
		<!-- 轮播图 -->
		<!-- 静态数据 -->
		<view class="lunbo">
			<swiper indicator-dots circular autoplay="true">
				<swiper-item>
					<image src="@/static/images/swiper01.png"></image>
				</swiper-item>
				<swiper-item>
					<image src="@/static/images/swiper02.png"></image>
				</swiper-item>
				<swiper-item>
					<image src="@/static/images/swiper03.png"></image>
				</swiper-item>
			</swiper>
		</view>
		<!-- 从接口取到数据动态渲染 -->
		<!-- <view class="lunbo">
			<swiper indicator-dots circular autoplay="true">
				<swiper-item v-for="item" in "swipers" :key="item.id">
					<image :src="item.image"></image>
				</swiper-item>
			</swiper>
		</view> -->
		<!-- 导航区域 -->
		<view class="nav">
			<view class="nav_item" v-for="(item,index) in navs" :key="index" @click="navItemClick(item.path)">
				<view :class="item.icon"></view>
				<text>{{item.title}}</text>
			</view>
		</view>
		<!-- 推荐商品 -->
		<view class="hot_goods">
			<view class="tit">推荐商品</view>
			<goods-list @goodsItemClick="goGoodsDetail"></goods-list>
			<!-- <goods-list :goods="goods" @goodsItemClick="goGoodsDetail"></goods-list> -->
		</view>
	</view>
</template>


<script>
	import goodsList from '@/components/goods-list/goods-list.vue'
	export default {
		data() {
			return {
				navs: [{
						icon: 'iconfont iconproduct-fill',
						title: 'uni超市',
						path: '/pages/goods/goods'
					},
					{
						icon: 'iconfont iconzhongjianren',
						title: '关于我们',
						path: '/pages/contact/contact'
					},
					{
						icon: 'iconfont iconpic1',
						title: '社区图片',
						path: '/pages/pics/pics'
					},
					{
						icon: 'iconfont iconvideo',
						title: '学习视频',
						path: '/pages/videos/videos'
					}
				]
			}
		},
		methods: {
			// 导航点击的处理函数
			navItemClick(url) {
				// console.log(url)
				uni.navigateTo({
					url
				})
			},
			//导航跳转到商品详情页
			goGoodsDetail(){
				uni.navigateTo({
					url:'/pages/goods-detail/goods-detail'
				})
			}
			
		},
		components:{
			"goods-list":goodsList
		}
	}
	// export default {
	// 	data() {
	// 		return {
	// 			swipers: [],
	// 			goods: []
	// 		}
	// 	},
	// 	onLoad() {
	// 		this.getSwipers(),
	// 			this.getHotGoods()
	// 	}
	// 	methods: {
	// 		//获取轮播图数据
	// 		async getSwipers() {
	// 			const res = await this $myRequest({
	// 				url: '/api/getlunbo'
	// 			})
	// 			this.swipers = res.data.message;
	// 		}
	// 		//获取热门商品列表数据
	// 		async getSwipers() {
	// 			const res = await this $myRequest({
	// 				url: '/api/getgoods?pageindex=1'
	// 			})
	// 			this.goods = res.data.message;
	// 		},
	// 		//导航跳转到商品详情页
	// 		goGoodsDetail(id){
	// 			uni.navigateTo({
	// 				url:'/pages/goods-detail/goods-detail?id='+id
	// 			})
	// 		}
	// 	}
	// }
</script>

<style lang="scss">
	.lunbo {
		swiper {
			width: 750rpx;
			height: 380rpx;

			image {
				height: 100%;
				width: 100%;
			}
		}
	}

	/* iconfont.css */
	@import "@/static/font/iconfont.css";

	.nav {
		display: flex;

		&_item {
			width: 25%;
			text-align: center;

			view {
				width: 100rpx;
				height: 100rpx;
				background: $shop-color;
				border-radius: 60rpx;
				margin: 10px auto;
				line-height: 100rpx;
				color: #fff;
				font-size: 50rpx;
			}

			text {
				font-size: 30rpx;
			}
		}
	}

	.hot_goods {
		background: #eee;
		margin-top: 10rpx;
		overflow: hidden;

		.tit {
			height: 50rpx;
			line-height: 50rpx;
			color: $shop-color;
			text-align: center;
			letter-spacing: 20rpx;
			background: #fff;
			margin: 7rpx 0;
		}

		
	}
</style>
