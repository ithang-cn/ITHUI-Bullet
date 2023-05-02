/**
* ITHUI®
* ITHUI-Bullet 适用于升级&通知、任务说明、活动规则、置顶公告弹框，兼容小程序、APP、H5。
* Copyright (c) 2023 ITHANG All rights reserved.
* Licensed ( http://www.apache.org/licenses/LICENSE-2.0 )
* 复制使用请保留本段注释，感谢支持开源！
*
* 作者主页
* https://ithang.cn/
*
* 开源地址
* https://github.com/ithang-cn/ITHUI-Bullet
* https://gitee.com/ithang-cn/ITHUI-Bullet
*
*/

<template>
	<view class="ithui-bullet">
		<u-popup @click="handleCloseOnClickOverlay" :show="value" :zIndex="zIndex" :overlayOpacity="opacity"
			:closeOnClickOverlay="closeOnClickOverlay" mode="center" bgColor="transparent">
			<view class="bullet-box">
				<view class="top">
					<view class="bg">
						<image src="@/static/style-one/top-bg.png" />
					</view>
					<view class="sub">
						<view class="icon">
							<image :src="icon" />
						</view>
						<view class="title">{{title}}</view>
					</view>
				</view>
				<scroll-view :scroll-top="scrollTop" :scroll-y="true" class="scroll-Y" @scroll="scroll">
					<view class="content">
						<rich-text :nodes="content"></rich-text>
					</view>
				</scroll-view>
				<view class="button">
					<u-button @click="handleOK" shape="circle" :color="buttonColor" :text="buttonText"></u-button>
				</view>
			</view>
			<view class="bullet-close">
				<u-icon @click="handleClose" name="close-circle" color="#fff" size="34"></u-icon>
			</view>
		</u-popup>
	</view>
</template>

<script>
	export default {
		name: "ithui-bullet-two",
		props: {
			value: {
				type: Boolean,
				default: false
			},
			zIndex: {
				type: String | Number,
				default: 10086
			},
			opacity: {
				type: String | Number,
				default: 0.5
			},
			closeOnClickOverlay: {
				type: Boolean,
				default: false
			},
			icon: {
				type: String,
				default: ''
			},
			title: {
				type: String,
				default: '标题'
			},
			content: {
				type: String,
				default: ''
			},
			buttonColor: {
				type: String,
				default: 'linear-gradient(to right, #0db5f0, #2d95f1)'
			},
			buttonText: {
				type: String,
				default: '确定'
			}
		},
		data() {
			return {
				scrollTop: 0,
				old: {
					scrollTop: 0
				}
			};
		},
		methods: {
			handleOK() {
				this.$emit('input', false);
				this.$emit('confirm');
			},
			handleCloseOnClickOverlay() {
				if (this.closeOnClickOverlay) {
					this.$emit('input', false);
					this.$emit('close');
				}
			},
			handleClose() {
				this.$emit('input', false);
				this.$emit('cancel');
			},
			scroll(e) {
				this.old.scrollTop = e.detail.scrollTop
			},
		}
	}
</script>

<style lang="scss" scoped>
	.ithui {
		&-bullet {
			.bullet {
				&-box {
					background-color: #fff;
					width: 640rpx;
					height: 65vh;
					border-radius: 20rpx;

					.top {
						width: 640rpx;
						height: 260rpx;

						.bg {
							width: 640rpx;
							height: 260rpx;

							image {
								width: 100%;
								height: 100%;
								border-radius: 20rpx 20rpx 0 0;
							}
						}

						.sub {
							width: 640rpx;
							height: 260rpx;
							position: relative;
							top: -260rpx;
							text-align: center;
							color: #fff;
							font-size: 36rpx;
							letter-spacing: 5rpx;

							.icon {
								margin-top: 20rpx;
								margin-bottom: 10rpx;
								border-radius: 120rpx;

								image {
									width: 120rpx;
									height: 120rpx;
									border-radius: 120rpx;
								}
							}
						}
					}


					.scroll-Y {
						margin-top: 15rpx;
						height: 35vh;

						.content {
							margin: 0 30rpx;
						}
					}

					.button {
						margin: 20rpx 100rpx;
					}
				}

				&-close {
					margin-top: 20rpx;
					display: flex;
					justify-content: center;
				}
			}
		}
	}
</style>