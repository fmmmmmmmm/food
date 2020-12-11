<template>
	<view class="content">
		<uni-search-bar :radius="100" placeholder="今天想吃点啥？" @confirm="search"></uni-search-bar>
		<view class="swiper">轮播图</view>
		<!-- <swiper class="swiper" indicator-dots :autoplay="true" :interval="3000" circular>
			<swiper-item v-for="item in swipers" :key="item.id">
				<image :src="item.imageUrl"></image>
			</swiper-item>
		</swiper> -->
		<uni-grid :column="4" :showBorder="false">
			<uni-grid-item v-for="item in navs" :key="item.title">
				<view :class="item.icons" @click="goZaoju(item)"></view>
				<text>{{item.title}}</text>
			</uni-grid-item>
		</uni-grid>
	</view>
</template>

<script>
	import uniSearchBar from '@/components/uni/uni-search-bar/uni-search-bar.vue';
	import uniGrid from "@/components/uni/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni/uni-grid-item/uni-grid-item.vue";
	export default {
		components: {
			uniSearchBar,
			uniGrid,
			uniGridItem
		},
		data() {
			return {
				swipers: [],
				navs: [{
						icons: "t-icon t-icon-guotiex",
						title: "灶具菜谱",
						path: "/pages/zaoju/zaoju"
					},
					{
						icons: "t-icon t-icon-wan",
						title: "烤箱菜谱",
						path: "/pages/zaoju/zaoju"
					},
					{
						icons: "t-icon t-icon-xiaolongbao",
						title: "蒸汽炉菜谱",
						path: "/pages/zaoju/zaoju"
					},
					{
						icons: "t-icon t-icon-xiaolongbao",
						title: "微波炉菜谱",
						path: "/pages/zaoju/zaoju"
					}
				]
			}
		},
		onLoad() {
			
		},
		methods: {
			goZaoju(item) {
				uni.navigateTo({
					url: item.path
				})
			}
		}
	}
</script>

<style lang="scss">
	.content {
		.swiper {
			width: 100%;
			height: 380rpx;
			background-color: orangered;
		}

		.uni-grid-item {
			text-align: center;

			.t-icon {
				line-height: 90rpx;
				width: 110rpx;
				height: 110rpx;
				margin: 10rpx auto;
				font-size: 25px;
			}

			text {
				font-size: 12px;
			}
		}
	}
</style>
