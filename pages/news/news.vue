<template>
	<view>
		<news-item @itemClick="goDetail"></news-item>
		<!-- <news-item @itemClick="goDetail" :list="list"></news-item> -->
	</view>
</template>

<script>
	import newsList from '@/components/news_item/news_item.vue'
	//静态
	export default{
		components:{
			"news-item":newsList
		},
		methods:{
			goDetail(){
				uni.navigateTo({
					url:'/pages/news-detail/news-detail'
				})
			}
		}
	}
	// //动态
	// export default {
	// 	data() {
	// 		return {
	// 			newsList:[]
	// 		};
	// 	},
	// 	methods:{
	// 		async getNews(){
	// 			const res = await this.$myRequest({
	// 				url:'/api/getnewslist'
	// 			})
	// 			console.log(res)
	// 			this.newsList = res.data.message
	// 		},
	// 		goDetail(id){
	// 			console.log(id)
	// 			uni.navigateTo({
	// 				url:'/pages/news-detail/news-detail?id='+id
	// 			})
	// 		}
	// 	},
	// 	onLoad(){
	// 		this.getNews()
	// 	}
	// }
</script>

<style lang="scss">
	
</style>
