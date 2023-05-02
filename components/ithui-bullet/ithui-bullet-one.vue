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
			<view class="bullet-box" :style="{borderColor,backgroundColor:bgColor}">
				<view class="top">
					<view class="title" :style="{color: titleColor}">{{title}}</view>
				</view>
				<scroll-view :scroll-top="scrollTop" :scroll-y="true" class="scroll-Y" @scroll="scroll">
					<view class="content" :style="{color: color}">
						<rich-text :nodes="content"></rich-text>
					</view>
				</scroll-view>
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
			title: {
				type: String,
				default: '标题'
			},
			color: {
				type: String,
				default: '#333'
			},
			titleColor: {
				type: String,
				default: '#7d4802'
			},
			borderColor: {
				type: String,
				default: '#fad489'
			},
			bgColor: {
				type: String,
				default: '#fffdf1'
			},
			content: {
				type: String,
				default: ''
			},
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
					width: 620rpx;
					height: 60vh;
					border-radius: 20rpx;
					border-width: 10rpx;
					border-style: solid;

					.top {
						font-size: 38rpx;
						text-align: center;
						font-weight: bold;
						margin-top: 60rpx;
					}

					.scroll-Y {
						margin-top: 20rpx;
						height: 48vh;

						.content {
							margin: 0 30rpx;
						}
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