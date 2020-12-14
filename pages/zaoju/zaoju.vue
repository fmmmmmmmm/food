<template>
	<view>
		<image src="../../static/tabs/1.png" mode=""></image>
		<view class="recommend">
			<view class="" >
				<view class="recommend-img">
					<image src="../../static/tabs/1.png" mode=""></image>
				</view>
				<view class="recommend-foot">
					<text>111111</text>
					<text>1111111</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import {
		myRequest,
		myRequestPost
	} from "@/utils/request.js"
	export default {
		data() {
			return {

			};
		},
		onLoad() {
			this.getZaoJu()
		},
		methods:{
			async getZaoJu(){
				let res=await myRequestPost("/api/cookbook/details/get-by-id")
				console.log(res)
				}
			}
	}
</script>

<style lang="less">
	image{
		width: 100%;
	}
    .recommend {
		width: 95%;
		margin: 20rpx auto;
		.recommend-img {
			margin: 0 auto;

			image {
				width: 712rpx;
				height: 370rpx;
				border-radius: 20rpx;
			}
		}

		.recommend-foot {
			display: flex;
			justify-content: space-between;
			color: #885e46;
			font-family: sans-serif;
		}
	}
</style>
