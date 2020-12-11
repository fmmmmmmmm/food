<template>
	<view class="detail">
		<image :src="menuDetail.imgLarge" mode=""></image>
		<view class="contant-d">
			<view class="m-name">
				<view class="name-txt">
					{{menuDetail.name}}
				</view>
			</view>
			<text class="collect">收藏 {{menuDetail.collectCount}}</text>
			<view class="Intro">
				<view class="intro-txt">
					<text class="online">——</text>
					<text class="txt" style="color: #000000;">菜谱简介</text>
					<text class="online">——</text>
					<text class="fuhao">▼</text>
				</view>
				<text class="into-cont">{{menuDetail.introduction}}</text>
			</view>
			<view class="Metro">
				<view class="met-txt">
					<text class="online">——</text>
					<text class="txt">用料</text>
					<text class="online">——</text>
					<text class="fuhao">▼</text>
				</view>
				<view class="metire" v-for="item in menuDetail.materials.main" :key="item.name">
					<text class="name">{{item.name}}</text>
					<text class="standerWe">{{item.standardWeight}}{{item.standardUnit}}</text>
				</view>
				<view class="metire" v-for="item in menuDetail.materials.accessory" :key="item.name">
					<text class="name">{{item.name}}</text>
					<text class="standerWe">{{item.standardWeight}}{{item.standardUnit}}</text>
				</view>
			</view>
			<view class="Prep">
				<view class="pre-txt">
					<text class="online">——</text>
					<text class="txt">备菜步骤</text>
					<text class="online">——</text>
					<text class="fuhao">▼</text>
				</view>
				<view class="prepare" v-for="item in menuDetail.prepareSteps.steps" :key="item.id">
					<image :src="item.imgUrl" mode=""></image>
					<view class="stepss">
						<text class="no">
							<text style="font-size: 35rpx ;font-weight: 500;">{{item.no}}</text>
							<text style="color: #000000;">/</text>
							<text>{{menuDetail.prepareSteps.steps.length}}</text>
						</text>
						<text class="desc">{{item.desc}}</text>
					</view>
				</view>
			</view>
			<view class="Steps">
				<view class="step-txt">
					<text class="online">——</text>
					<text class="txt">做法步骤</text>
					<text class="online">——</text>
					<text class="fuhao">▼</text>
				</view>
				<view class="prepare" v-for="item in menuDetail.steps" :key="item.id">
					<image :src="item.image" mode=""></image>
					<view class="stepss">
						<text class="no">
							<text style="font-size: 35rpx ;font-weight: 500;">{{item.no}}</text>
							<text style="color: #000000;">/</text>
							<text>{{menuDetail.steps.length}}</text>
						</text>
						<text class="desc">{{item.desc}}</text>
					</view>
					
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import {
		myRequestPost
	} from '@/utils/request.js'
	export default {
		data() {
			return {
				id: 0,
				menuDetail: []
			};
		},
		onLoad(option) {
			this.id = option.id
			console.log("pppppppp")
			this.getMenuDetail()
		},
		methods: {
			async getMenuDetail() {
				let result = await myRequestPost('/api/cookbook/details/get-by-id/', {
					"cookbookId": this.id
				})
				console.log(result.cookbook, "kkkkkkkkkk")
				this.menuDetail = result.cookbook
			},
		}
	}
</script>

<style lang="scss">
	.detail {
		display: flex;
		flex-direction: column;

		image {
			width: 100%;
			height: 500rpx;
		}

		.contant-d {
			margin: 0 20rpx;
			height: 100%;
			position: relative;

			.m-name {
				position: absolute;
				width: 60rpx;
				padding: 10rpx;
				left: 50%;
				margin-left: -30rpx;
				margin-top: -120rpx;
				background-color: rgba($color: #fff, $alpha: 0.81);
				border-radius: 20rpx;

				.name-txt {
					padding: 13rpx 12rpx;
					border: 1rpx solid #000;
					font-size: 33rpx;
					border-radius: 20rpx;
					color: #000;
					line-height: 43rpx;
				}
			}

			.collect {
				display: inline-block;
				position: absolute;
				top: 50rpx;
				right: 0;
				color: #666;
				font-size: 23rpx;
				font-weight: 700;
			}

			.Intro {
				margin-top: 120rpx;
				width: 100%;
				height: 300rpx;

				.into-cont {
					font-size: 27rpx;
					color: #555;
					letter-spacing: 2rpx;
					line-height: 40rpx;
				}
			}

			.intro-txt,
			.met-txt,
			.pre-txt,
			.step-txt {
				text-align: center;
				color: orange;

				.txt {
					font-size: 35rpx;
					font-weight: 520;
					padding: 0 20rpx;
				}

				.fuhao {
					display: block;
				}
			}

			.Metro {
				margin-top: 20rpx;

				.metire {
					border-bottom: 1rpx solid #999;
					padding: 10rpx 100rpx;

					.name {}

					.standerWe {
						display: inline-block;
						float: right;
					}
				}
			}

			.Prep,
			.Steps {
				padding: 0 20rpx;

				.prepare {
					width: 100%;

					image {
						height: 550rpx;
					}
					.stepss{
						padding: 15rpx;
						.no{
							text{
								font-size: 28rpx;
								color: orange;
							}
						}
						.desc{
							padding-left: 5rpx;
							letter-spacing: 2rpx;
							line-height: 40rpx;
							color: #666;
						}
					}
					
				}
				
			}

			.Prep {
				margin-top: 10rpx;
			}

			.Steps {
				margin-top: 40rpx;
			}
		}
	}

	page {
		font-size: 27rpx;
		font-weight: 400;
	}
</style>
