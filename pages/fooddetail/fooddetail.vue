<template>
	<view>
		<image :src="foodDetail.imgLarge" mode=""></image>
		<view class="continer">
			<view class="box">
				<view class="name">
					{{foodDetail.name}}
				</view>
			</view>
			<view class="brief">
				<view class="text">——菜谱简介——</view>
				<view class="brief_more">{{foodDetail.introduction}}</view>
			</view>

		</view>


	</view>
</template>

<script>
	import {
		myRequestPost
	} from "@/utils/request.js";
	export default {
		data() {
			return {
				id: "",
				foodDetail: {}
			};
		},
		onLoad(options) {
			this.id = options.id;
			this.getFoodDetail();
		},
		methods: {
			async getFoodDetail() {
				const res = await myRequestPost("/api/cookbook/details/get-by-id", {
					"cookbookId": this.id,
				});
				console.log(typeof(res));
				this.foodDetail = res.cookbook;

				console.log(this.foodDetail, "kkkkkkkkkkkkkkkkkkkkkk");

			}
		}

	}
</script>

<style lang="less">
	page {
		width: 100%;
		height: 100%;
		font-family: "楷体";

		image {
			width: 750rpx;
			height: 450rpx;
		}

		.continer {
			width: 700rpx;
			margin: 20rpx;

			.box {
				width: 100rpx;
				height: 300rpx;
				background-color: rgba(255, 255, 255, 0.5);
				border-radius: 20rpx;
				position: relative;
				left: 50%;
				margin-left: -50rpx;
				top: 50%;
				margin-top: -150rpx;

				.name {
					margin: 0 auto;
					width: 80rpx;
					height: 250rpx;
					border: 1px solid;
					border-radius: 30rpx;
					font-size: 42rpx;
					text-align: center;

				}
			}

			.brief {
				.text {
					font-size: 40rpx;
					width: 400rpx;
					height: 40rpx;
					line-height: 40rpx;
					margin:0 auto;
					text-align: center;
					font-weight: bold;
				}
				.brief_more{
					margin-top: 20rpx;
				}
			}
		}
	}

</style>
