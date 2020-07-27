<template>
	<view class="contact">
		<image class="img" src="@/static/images/contact.png"></image>
		<view class="info">
			<view @click="phone">联系电话：1008611（点击拨打）</view>
			<view>住址：****************************************</view>
		</view>
		<map class="map" :longitude="longitude" :latitude="latitude" :markers="markers" :scale="scale"></map>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				longitude:114.355346,//经度
				latitude:30.590358,//纬度
				scale:13,//缩放
				markers:[
					{
						longitude:114.355346,//经度
						latitude:30.590358,//纬度
						iconPath:'../../static/images/dian.png',
						width:30,
						height:30
					}
				]//标记点
			};
		},
		methods:{
			phone(){
				uni.makePhoneCall({
					phoneNumber:'1008611'
				})
			}
		}
	}
</script>

<style lang="scss">
	.contact{
		.img{
			width:750rpx;
			height:300rpx;
		}
		.info{
			padding:10rpx 20rpx;
			font-size: 30rpx;
			view{
				line-height: 80rpx;
				border-bottom:1px solid #eee;
			}
		}
		.map{
			width:750rpx;
			height:750rpx;
		}
	}
</style>
