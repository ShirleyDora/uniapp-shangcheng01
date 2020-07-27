<template>
	<view class="goods_list">
		<goods-list @goodsItemClick="goGoodsDetail"></goods-list>
		<!-- <goods-list :goods="goods" @goodsItemClick="goGoodsDetail"></goods-list> -->
		<!-- <view class="isOver" v-if="flag">数据到底了</view> -->
	</view>
</template>

<script>
	import goodsList from '@/components/goods-list/goods-list.vue'
	export default {
		components:{
			"goods-list":goodsList
		},
		methods:{
			//导航跳转到商品详情页
			goGoodsDetail(){
				uni.navigateTo({
					url:'/pages/goods-detail/goods-detail'
				})
			}
		}
		
		
		// 下拉加载
		// onReachBottom(){
		// 	console.log(this.goods.length)
		// 	if(this.goods.length<this.pageindex*10) return this.flag = true
		// 	console.log('触底了')
		// 	this.pageindex++;
		// 	this.getGoodsList()
		// }
		//下拉刷新
		// onPullDownRefresh(){
		// 	console.log('下拉刷新了')
		// 	this.pageindex = 1
		// 	this.goods = []
		// 	this.flag = false
		// 	setTimeout(()=>{
		// 		this.getGoodsList(()=>{
		// 			uni.stopPullDownRefresh()
		// 		})
		// 	},1000)
		// }
		// data() {
		// 	return {
		// 		pageindex:1,
		// 		goods:[],
		// 		flag:false
		// 	};
		// },
		// methods:{
		// 	//获取商品列表的数据
		// 	async getGoodsList(callBack){
		// 		const res = await this.$myRequest({
		// 			url:'/api/getgoods?pageindex='+this.pageindex
		// 		})
		// 		// console.log(res)
		// 		// this.goods = res.data.message
		// 		this.goods = [...this.goods,...res.data.message]
		// 		callBack || callBack()
		// 	},
		//  //导航跳转到商品详情页
		// 	goGoodsDetail(id){
		// 		uni.navigateTo({
		// 			url:'/pages/goods-detail/goods-detail?id='+id
		// 		})
		// 	}
		// },
		// //调用方法
		// onLoad(){
		// 	this.getGoodsList()
		// }
	}
</script>

<style lang="scss">
 .goods_list{
	 background: #eee;
 }
 .isOver{
	 width:100%;
	 height:50rpx;
	 line-height: 50rpx;
	 text-align: center;
	 font-size:28rpx;
 }
</style>
