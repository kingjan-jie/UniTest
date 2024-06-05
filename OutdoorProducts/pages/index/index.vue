<template>
	<view class="layout indexBg">
		<view class="head">
			<swiper indicator-dots circular>
				<swiper-item v-for="item in BannerList" :key="item.goods_id">
					<image :src="item.image_src" mode="aspectFill"></image>
				</swiper-item>
			</swiper>
		</view>

		<view class="horn">
			<!-- 图标 -->
			<view class="hornIcon">
				<uni-icons type="sound-filled" size="20" color="#4986f7"></uni-icons>
			</view>
			<!-- 内容 -->
			<view class="content">
				<swiper vertical autoplay interval="1500" duration="300" circular>
					<swiper-item v-for="item in 5">
						<navigator url="">
							我是占位符我是占位符我是占位符我是占位符我是占位符我是占位符我是占位符我是占位符我是占位符
						</navigator>
					</swiper-item>
				</swiper>
				
			</view>
			<!-- 想右边图标 -->
			<view class="iconRight ">
				<uni-icons type="right" size="20" color="#4986f7"></uni-icons>
			</view>
		</view>

		<view class="body">

		</view>

		<view class="bottom">

		</view>
	</view>
</template>

<script setup>
	import {
		ref
	} from 'vue';
	//定义变量
	const BannerList = ref([]);

	const getSwiperBanner = async () => {
		let res = await uni.request({
			url: "https://api-hmugo-web.itheima.net/api/public/v1/home/swiperdata"
		}).then(res => {
			if (res.data.meta.status === 200) {
				BannerList.value = res.data.message
			}
		}).finally(() => {
			console.log("接口被访问了");
		})
		// console.log(res)
	}
	getSwiperBanner();
</script>

<style lang="scss" scoped>
	.layout {

		.head {
			//父级先定义大小
			width: 750rpx;
			padding: 50rpx 20rpx;

			swiper {
				width: 100%;
				height: 30vh;

				&-item {
					width: 100%;
					height: 100%;

					image {
						width: 100%;
						height: 100%;
						border-radius: 30rpx;
					}
				}
			}
		}

		.horn {
			display: flex;
			width: 750rpx;
			height: 80rpx;
			align-items: center;
			justify-content: center;
			background-color: #fff;
			border-radius: 30rpx;
			padding: 0 20rpx;
			.hornIcon {
				padding-left: 5rpx;
				/* :deep(){
					.uni-icons{
						color: $show-base-color !important;
					}
				} */
				
			}

			.content {
				width: 750rpx;
				height: 50rpx;
				swiper{
					width: 100%;
					height: 100%;
					&-item{
						width: 100%;
						height: 100%;
						navigator{
							white-space: nowrap;
							overflow: hidden;
							text-overflow: ellipsis;
							padding: 0 10rpx;
						}
					}
				}
			}

			.iconRight {
				padding-left: 5rpx;
			}
		}

		.body {}

		.bottom {}

	}
</style>