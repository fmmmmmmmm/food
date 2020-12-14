<template>
	<view class="box">

		<view class="lp">
			<video :src="userinfo.playUrl"></video>
		</view>
		<view class="bottom">
			<view class="bl">{{userinfo.desc}}</view>
			<view class="br">观看次数：{{userinfo.videoWatchcount}}</view>
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
				id: "",
				videoDetail: {},
				userinfo:""
			}
		},
		// Params:{
		// 	playUrl:"",
		// 	seriesId:"",
		// },
		onLoad() {
		   const userinfo = uni.getStorageSync("userinfo");
		   this.userinfo=userinfo
		   // console.log(userinfo)
		   // console.log(userinfo.playUrl)
		   // console.log(userinfo.videoWatchcount)
		  },
	}
</script>

<style>
	.bl {
		float: left
	}

	.br {
		float: right
	}
</style>
