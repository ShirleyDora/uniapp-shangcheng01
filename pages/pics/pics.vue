<template>
	<view class="pics">
		<!-- 静态 -->
		<scroll-view class="left" scroll-y>
			<view class="active">家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
			<view>家居生活</view>
		</scroll-view>
		<scroll-view class="right" scroll-y>
			<view class="item">
				<image src="../../static/images/jiaju.png"></image>
				<text>顾家简约现代轻奢真皮沙发客厅北欧小户型组合皮艺皮沙发家具</text>
			</view>
			<view class="item">
				<image src="../../static/images/jiaju.png"></image>
				<text>顾家简约现代轻奢真皮沙发客厅北欧小户型组合皮艺皮沙发家具</text>
			</view>
			<view class="item">
				<image src="../../static/images/jiaju.png"></image>
				<text>顾家简约现代轻奢真皮沙发客厅北欧小户型组合皮艺皮沙发家具</text>
			</view>
		</scroll-view>
		<!-- 动态 -->
		<!-- <scroll-view class="left" scroll-y>
			<view 
				@click="leftClickHandle(index,item.id)" 
				:class="active === index?'active':'" 
				v-for="(item,index) in cates" 
				:key="item.id">
					{{item.title}}
			</view>
		</scroll-view> 
		<scroll-view class="right" scroll-y>
			<view class="item" v-for="item in secondData" :key="item.id">
				<image @click="previewImg(item.img_url)" :src="item.img_url"></image>
				<text>{{item.title}}</text>
			</view>
			<text v-if="secondData.length === 0">暂无数据</text>
		</scroll-view> -->
	</view>

</template>

<script>
	export default {
		data() {
			return {
				active:0,
				cates:[],
				secondData:[]
			};
		},
		methods:{
			async getPicsCate(){
				const res = this.$myRequest({
					url:'/api/getimgcategory'
				})
				// console.log(res)
				this.cates = res.data.message
				this.leftClickHandle(0,this.cates[0].id)//默认获取数据
			},
			async leftClickHandle(index,id){
				this.active = index;
				// console.log(id)
				//获取右侧数据
				const res = await this.$myRequest({
					url:'/api/getimages/'+id
				})
				console.log(res)
				this.secondData = res.data.message
			},
			previewImg(current){
				const urls = this.secondData.map(item=>{
					return item.img_url
				})
				console.log(urls)
				uni.previewImage({
					current,
					urls
				})
			}
		},
		onLoad(){
			this.getPicsCate()
		}
	}
</script>

<style lang="scss">
	page {
		height: 100%;
	}

	.pics {
		height: 100%;
		display:flex;
		.left {
			width: 200rpx;
			height: 100%;
			border-right:1px solid #eee;
			view {
				height: 60px;
				line-height: 60px;
				color: #333;
				text-align: center;
				font-size:30rpx;
				border-top:1px solid #eee;
			}
			.active{
				background:$shop-color;
				color:#fff;
			}
		}
		.right{
			height:100%;
			width:520rpx;
			margin:10rpx auto;
			.item{
				image{
					width:520rpx;
					height:520rpx;
					border-radius:5px;
				}
				text{
					font-size:30rpx;
					line-height:60rpx;
				}
			}
		}
	}
</style>
