<template>
	<view class="tab_control">
		<view class="tab_item"
			v-for="(item,index) in title"
			:key='index'
			:class="{active: index === currentIndex}"
			@click="tabClick(index)">
			<text>{{item}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				currentIndex: 0
			}
		},
		props: {
			title: {
				type: Array,
				default () {
					return []
				}
			}
		},
		methods: {
			tabClick(index) {
				this.currentIndex = index
				this.$emit('tabClick',index)
			}
		}
	}
</script>

<style>
	.tab_control {
		display: flex;
		margin-bottom: 16rpx;
	}

	.tab_item {
		flex: 1;
		text-align: center;
		height: 80rpx;
		line-height: 80rpx;
		font-size: 32rpx;
	}

	.active {
		color: #ff5777;
	}

	.tab_item.active text {
		padding: 16rpx 10rpx;
		border-bottom: 6rpx solid #FF5777;
	}
</style>
