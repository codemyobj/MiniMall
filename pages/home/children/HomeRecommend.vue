<template>
	<view class="recommend">
		<view v-for="(item,index) in recommend" :key='index'>
			<view class="recommend-item">
				<image :src="item.image" />
				<text>{{item.title}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			recommend: {
				type: Array,
				default () {
					return []
				}
			}
		}
	}
</script>

<style>
	.recommend {
		display: flex;
		margin-top: 40rpx;
		border-bottom: 10rpx solid #eee;
		padding-bottom: 40rpx;
	}
	
	.recommend-item {
		flex: 1;
		text-align: center;
	} 
	
	.recommend-item image {
		width: 160rpx;
		height: 160rpx;
		margin-bottom: 10rpx;
	}
	
	.recommend-item text {
		font-size: 30rpx;
		color: #555;
	}
</style>
