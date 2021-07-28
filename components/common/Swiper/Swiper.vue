<template>
	<swiper
		circular
		autoplay
		indicator-dots
		indicator-active-color="#ff5777"
		:interval="3000"
		:duration="500">
		<swiper-item
			v-for="(item,index) in banner"
			:key='index'>
			<view class="swiper">
				<image
					:src="item.image"
					mode="widthFix"></image>
			</view>
		</swiper-item>
	</swiper>
</template>

<script>
	export default {
		props: {
			banner: {
				type: Array,
				default () {
					return []
				}
			}
		}
	}
</script>

<style>
	.swiper image {
		width: 100%;
	}
</style>
