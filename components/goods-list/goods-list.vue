<template>
	<view>
		<!-- 静态数据 -->
		<view class="goods_list">
			<view class="goods_item" @click="navigator">
				<image src="@/static/images/shop01.png"></image>
				<view class="price">
					<text>￥2199</text>
					<text>￥2499</text>
				</view>
				<view class="name">
					<text>500ml网红水果茶杯子 大容量带盖饮料杯果汁杯</text>
				</view>
			</view>
			<view class="goods_item" @click="navigator">
				<image src="@/static/images/shop01.png"></image>
				<view class="price">
					<text>￥2199</text>
					<text>￥2499</text>
				</view>
				<view class="name">
					<text>500ml网红水果茶杯子 大容量带盖饮料杯果汁杯</text>
				</view>
			</view>
			<view class="goods_item" @click="navigator">
				<image src="@/static/images/shop01.png"></image>
				<view class="price">
					<text>￥2199</text>
					<text>￥2499</text>
				</view>
				<view class="name">
					<text>500ml网红水果茶杯子 大容量带盖饮料杯果汁杯</text>
				</view>
			</view>
			<view class="goods_item" @click="navigator">
				<image src="@/static/images/shop01.png"></image>
				<view class="price">
					<text>￥2199</text>
					<text>￥2499</text>
				</view>
				<view class="name">
					<text>500ml网红水果茶杯子 大容量带盖饮料杯果汁杯</text>
				</view>
			</view>
			<view class="goods_item" @click="navigator">
				<image src="@/static/images/shop01.png"></image>
				<view class="price">
					<text>￥2199</text>
					<text>￥2499</text>
				</view>
				<view class="name">
					<text>500ml网红水果茶杯子 大容量带盖饮料杯果汁杯</text>
				</view>
			</view>
			<view class="goods_item" @click="navigator">
				<image src="@/static/images/shop01.png"></image>
				<view class="price">
					<text>￥2199</text>
					<text>￥2499</text>
				</view>
				<view class="name">
					<text>500ml网红水果茶杯子 大容量带盖饮料杯果汁杯</text>
				</view>
			</view>
			<view class="goods_item" @click="navigator">
				<image src="@/static/images/shop01.png"></image>
				<view class="price">
					<text>￥2199</text>
					<text>￥2499</text>
				</view>
				<view class="name" @click="navigator">
					<text>500ml网红水果茶杯子 大容量带盖饮料杯果汁杯</text>
				</view>
			</view>
			<view class="goods_item" @click="navigator">
				<image src="@/static/images/shop01.png"></image>
				<view class="price">
					<text>￥2199</text>
					<text>￥2499</text>
				</view>
				<view class="name">
					<text>500ml网红水果茶杯子 大容量带盖饮料杯果汁杯</text>
				</view>
			</view>
		</view>
		<!-- 从接口取到数据动态渲染 -->
		<!-- <view class="goods_list">
			<view class="goods_item" v-for="item in goods" :key="item.id" @click="navigator">
				<image :src="item.img_url"></image>
				<view class="price">
					<text>￥{{item.sell_price}}</text>
					<text>￥{{item.market_price}}</text>
				</view>
				<view class="name">
					<text>{{item.title}}</text>
				</view>
			</view>
		</view> -->
	</view>
</template>

<script>
	export default {
		 // props:['goods'],
		 methods:{
			 navigator(){
				 this.$emit('goodsItemClick')
			 }
		 }
	}
</script>

<style lang="scss">
	.goods_list {
		padding: 0 15rpx;
		display: flex; //横向排列
		flex-wrap: wrap; //换行
		justify-content: space-between; //设置间距
	
		.goods_item {
			background: #fff;
			width: 355rpx;
			margin: 10rpx 0;
			padding: 15rpx;
			box-sizing: border-box;
	
			image {
				width: 80%;
				height: 150rpx;
				margin: auto; //图片居中
				display: block;
			}
		}
	
		.price {
			color: $shop-color;
			font-size: 36rpx;
			margin: 20rpx 0 5rpx 0;
	
			text:nth-child(2) {
				color: #ccc;
				font-size: 28rpx;
				margin-left: 7rpx;
				text-decoration: line-through; //注释斜线
			}
		}
	
		.name {
			font-size: 28rpx;
			line-height: 50rpx;
			padding: 10rpx 0 15rpx 0;
		}
	}
</style>
