<template>
	<view>
		<swiper :banner='banner'/>
		<home-recommend :recommend='recommend'/>
	</view>
</template>

<script>
	import Swiper from '@/components/common/Swiper/Swiper.vue'
	import HomeRecommend from './children/HomeRecommend.vue'
	
	import {
		getMultiData
	} from '@/service/home.js'

	export default {
		data() {
			return {
				banner: [],
				recommend: []
			}
		},
		components: {
			Swiper,
			HomeRecommend
		},
		onLoad(options) {
			getMultiData().then(res => {
				// 取出轮播图和推荐数据
				const data = res.data.data	
				this.banner = data.banner.list
				this.recommend = data.recommend.list
			})
		},
	}
</script>

<style>
	
</style>
