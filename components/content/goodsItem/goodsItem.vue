<template>
	<view class="goods">
		<view class="goods-item"
			v-for="(item,index) in goods"
			:key='index'>
			<image :src="item.image"
				mode="widthFix" />
				{{item.title}}
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			goods: {
				type: Array,
				default () {
					return []
				}
			}
		}
	}
</script>

<style>
</style>
