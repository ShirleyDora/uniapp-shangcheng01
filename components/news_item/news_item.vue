<template>
	<view>
		<views class="news">
			<!-- 静态 -->
			<view class="news_item" @click="navigator">
				<image src="@/static/images/news.png"></image>
				<view class="right">
					<view class="tit">
						7月新房销售突破2万亿，新开工面积创历史新高
					</view>
					<view class="info">
						<text>发表时间：</text>
						<text>浏览：</text>
					</view>
				</view>
			</view>
			<view class="news_item" @click="navigator">
				<image src="@/static/images/news.png"></image>
				<view class="right">
					<view class="tit">
						7月新房销售突破2万亿，新开工面积创历史新高
					</view>
					<view class="info">
						<text>发表时间：</text>
						<text>浏览：</text>
					</view>
				</view>
			</view>
			<view class="news_item" @click="navigator">
				<image src="@/static/images/news.png"></image>
				<view class="right">
					<view class="tit">
						7月新房销售突破2万亿，新开工面积创历史新高
					</view>
					<view class="info">
						<text>发表时间：</text>
						<text>浏览：</text>
					</view>
				</view>
			</view>
			<view class="news_item" @click="navigator">
				<image src="@/static/images/news.png"></image>
				<view class="right">
					<view class="tit">
						7月新房销售突破2万亿，新开工面积创历史新高
					</view>
					<view class="info">
						<text>发表时间：</text>
						<text>浏览：</text>
					</view>
				</view>
			</view>
			<view class="news_item" @click="navigator">
				<image src="@/static/images/news.png"></image>
				<view class="right">
					<view class="tit">
						7月新房销售突破2万亿，新开工面积创历史新高
					</view>
					<view class="info">
						<text>发表时间：</text>
						<text>浏览：</text>
					</view>
				</view>
			</view>
			<view class="news_item" @click="navigator">
				<image src="@/static/images/news.png"></image>
				<view class="right">
					<view class="tit">
						7月新房销售突破2万亿，新开工面积创历史新高
					</view>
					<view class="info">
						<text>发表时间：</text>
						<text>浏览：</text>
					</view>
				</view>
			</view>
			<view class="news_item" @click="navigator">
				<image src="@/static/images/news.png"></image>
				<view class="right">
					<view class="tit">
						7月新房销售突破2万亿，新开工面积创历史新高
					</view>
					<view class="info">
						<text>发表时间：</text>
						<text>浏览：</text>
					</view>
				</view>
			</view>
			<!-- 动态 -->
			<!-- <view class="news_item" @click="navigator" v-for="item in newsList" :key="item.id">
				<image :src="item.img_url"></image>
				<view class="right">
					<view class="tit">
						{{item.title}}
					</view>
					<view class="info">
						<text>发表时间：{{item.add_time | formatDate}}</text>
						<text>浏览：{{item.click}}</text>
					</view>
				</view>
			</view> -->
		</views>
	</view>
	
</template>

<script>
	export default {
		props:['list'],
		//格式化日期格式
		filters:{
			formatDate(date){
				console.log(date)
				const nDate = new Date(date)
				console.log(nDate)
				const year = nDate.getFullYear()
				const month = nDate.getMonth().toString().padStart(2,0)//满足两位数，不满足加0
				const day = nDate.getDay().toString().padStart(2,0)
				console.log(year,month,day)
				return year+'-'+month+'-'+day
			}
		},
		methods:{
			navigator(){
				this.$emit('itemClick')
			}
		}
	}
</script>

<style lang="scss">
.news {
		&_item {
			display: flex;
			padding: 10rpx 20rpx;
			border-bottom: 1px solid $shop-color;

			image {
				min-width: 200rpx;
				max-width: 200rpx;
				height: 150rpx;
			}

			.right {
				margin-left: 15rpx;
				display: flex;
				flex-direction: column;
				justify-content: space-between;

				.tit {
					font-size: 30rpx;
				}

				.info {
					font-size: 24rpx;

					text:nth-child(2) {
						margin-left: 30rpx;
					}
				}
			}
		}
	}
</style>
