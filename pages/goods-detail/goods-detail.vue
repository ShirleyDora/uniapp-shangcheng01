<template>
	<view>
		<view class="goods_detail">
			<swiper indicator-dots>
				<swiper-item>
					<image src="@/static/images/item01.png"></image>
				</swiper-item>
				<swiper-item>
					<image src="@/static/images/item02.png"></image>
				</swiper-item>
				<swiper-item>
					<image src="@/static/images/item03.png"></image>
				</swiper-item>
			</swiper>
			<view class="box1">
				<view class="price">
					<text>￥55</text>
					<text>￥198</text>
				</view>
				<view class="goods_name">
					90口径加厚一次性奶茶杯子塑料注塑带盖网红果汁饮料打包定制logo
				</view>
			</view>
			<view class="line"></view>
			<view class="box2">
				<view>货号：SD1000000000</view>
				<view>库存：200</view>
			</view>
			<view class="line"></view>
			<view class="box3">
				<view class="tit">详情介绍</view>
				<view class="content">内容</view>
			</view>
		</view>
		<view class="goods_nav">
			<uni-goods-nav :fill="true"  :options="options" :buttonGroup="buttonGroup"  @click="onClick" @buttonClick="buttonClick" />
		</view>
		<!-- 动态 -->
		<!-- <view class="goods_detail">
			<swiper indicator-dots>
				<swiper-item v-for="(item,index) in swipers" :key="index">
					<image :src="item.src"></image>
				</swiper-item>
			</swiper>
			<view class="box1">
					<view class="price">
						<text>￥{{info.sell_price}}</text>
						<text>￥{{info.market_price}}</text>
					</view>
					<view class="goods_name">
						{{info.title}}
					</view>
				</view>
				<view class="line"></view>
				<view class="box2">
					<view>货号：{{info.goods_no}}</view>
					<view>库存：{{info.stock_quantity}}</view>
				</view>
				<view class="line"></view>
				<view class="box3">
					<view class="tit">详情介绍</view>
					<view class="content">
						<rich-text :nodes="content">
						</rich-text>
					</view>
				</view>
			</view>
			<view class="goods_nav">
				<uni-goods-nav :fill="true"  :options="options" :buttonGroup="buttonGroup"  @click="onClick" @buttonClick="buttonClick" />
			</view>
		</view> -->
	</view>
</template>

<script>
	import uniGoodsNav from '@/components/uni-goods-nav/uni-goods-nav.vue'
	export default {
		components: {uniGoodsNav},
		data() {
			return {
				options: [{
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
				  }
				  ],
			
				id:0,
				swipers:[],
				info:{},
				content:''
			};
		},
		methods:{
			onClick (e) {
			  uni.showToast({
			    title: `点击${e.content.text}`,
			    icon: 'none'
			  })
			  console.log(e)
			},
			buttonClick (e) {
			  console.log(e)
			  this.options[2].info++
			},
			async getSwipers(){
				const res = await this.$myRequest({
					url:'/api/getthumimages/'+this.id
				})
				// console.log(res)
				this.swipers = res.data.message
			},
			async getDetailInfo(){
				const res = this.$myRequest({
					url:'/api/goods/getinfo'+this.id
				})
				// console.log(res)
				this.info = res.data.message[0]
			},
			async getDetailContent(){
				const res = this.$myRequest({
					url:'/api/goods/getdesc/'+this.id
				})
				// console.log(res)
				this.content = res.date.message[0].content;
			}
		},
		//获取网站地址栏的?id=**
		onLoad(options){
			// console.log(options)
			this.id = options.id
			this.getSwipers()
			this.getDetailInfo()
			this.getDetailContent()
		}
	}
</script>

<style lang="scss">
.goods_detail{
	swiper{
		height: 700rpx;
		image{
			width: 100%;
			height: 100%;
		}
	}
	.box1{
		padding:10px;
		.price{
			font-size:35rpx;
			color:$shop-color;
			line-height: 80rpx;
			text:nth-child(2){
				color:#ccc;
				font-size: 28rpx;
				text-decoration: line-through;
				margin-left:20rpx;
			}
		}
		.goods_name{
			font-size:32rpx;
			line-height: 60rpx;
		}
	}
	.box2{
		padding:0 10px;
		font-size:32rpx;
		line-height: 70rpx;
	}
	.box3{
		padding-bottom: 50px;
		.tit{
			font-size:32rpx;
			padding-left:10px;
			border-bottom:1px solid #eee;
			line-height:70rpx;
		}
		.content{
			padding:10px;
			font-size:28rpx;
			color:#333;
			line-height: 50rpx;
		}
	}
}
.line{
	height:10rpx;
	width:750rpx;
	background:#eee;
}
.goods_nav{
		position:fixed;
		bottom:0;
		width:100%;
}
</style>
