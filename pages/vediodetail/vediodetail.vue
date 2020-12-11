<template>
	<view>
		ddd
	</view>
</template>

<script>
	import {
			myRequestPost
		} from '@/utils/request.js'
		export default {
			data() {
				return {
					id:"",
					newsDetail:{}
				}
			},
			onLoad(options) {
				this.id = options.courseId;
				this.getNewsDetail();
			},
			methods: {
				async getNewsDetail() {
					const res = await myRequestPost("/ops/api/source/getLocalVideoList",
						{"userId":null,"pageNo":0,"pageSize":50}
					)
					this.newsDetail = res.datas;
				},
			},
			components: {
				
			}
		}
</script>

<style>
</style>
