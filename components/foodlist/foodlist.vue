<template>
	<view>
		<view @click="itemClick(item)">
			菜谱列表
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		methods: {
			itemClick(item) {
				uni.navigateTo({
					url: '/pages/goodsdetail/goodsdetail'
				})
			}
		}
	}
</script>

<style>
</style>
