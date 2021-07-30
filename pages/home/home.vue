<template>
	<view>
		<swiper :banner='banner' />
		<home-recommend :recommend='recommend' />
		<feature-view />
		<tab-control :title='titles'
			@tabClick='tabClick' />
		<goods-item :goods='goods[currentType].list'/>
	</view>
</template>

<script>
	import Swiper from '@/components/common/Swiper/Swiper.vue'
	import HomeRecommend from './children/HomeRecommend.vue'
	import FeatureView from './children/featureView.vue'
	import TabControl from '@/components/content/tabControl/tabControl.vue'
	import GoodsItem from '@/components/content/goodsItem/goodsItem.vue'

	import {
		getMultiData,
		getGoodsData
	} from '@/service/home.js'

	export default {
		data() {
			return {
				banner: [],
				recommend: [],
				titles: ['流行', '新款', '精选'],
				goods: {
					pop: {
						page: 0,
						list: []
					},
					new: {
						page: 0,
						list: []
					},
					sell: {
						page: 0,
						list: []
					}
				},
				currentType: 'pop'
			}
		},
		components: {
			Swiper,
			HomeRecommend,
			FeatureView,
			TabControl,
			GoodsItem
		},
		onLoad(options) {
			this._getMultidata()
			// 商品数据
			this._getGoodsData('pop')
			this._getGoodsData('new')
			this._getGoodsData('sell')
		},
		methods: {
			// --------------网络请求------------
			_getMultidata() {
				getMultiData().then(res => {
					// 取出轮播图和推荐数据
					const data = res.data.data
					this.banner = data.banner.list
					this.recommend = data.recommend.list
				})
			},
			_getGoodsData(type) {
				const page = this.goods[type].page + 1
				getGoodsData(type, page).then(res => {
					const data = res.data.data
					this.goods[type].list.push(...data.list)
				})
			},
			// ----------事件监听----------
			tabClick(index) {
				const types = ['pop','new','sell']
				this.currentType = types[index]
				console.log(this.currentType)
			},
		}
	}
</script>

<style>

</style>
