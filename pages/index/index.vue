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
	<view class="ithui-content">
		<view class="content">
			<!-- 样式一 -->
			<ithui-bullet-one v-model="showBullet.one" :content="content.one" title="活动规则" :closeOnClickOverlay="true"
				@cancel="e=>{handleCancel('一')}" @close="e=>{handleClose('一')}" />
			<!-- 样式二 -->
			<ithui-bullet-two v-model="showBullet.two" :content="content.two" title="齐聚圈子 共享欢乐"
				icon="https://static.ithang.cn/ITHUI/logo.jpg" buttonText="去完成" :closeOnClickOverlay="true"
				@confirm="e=>{handleConfirm('二')}" @cancel="e=>{handleCancel('二')}" @close="e=>{handleClose('二')}" />
		</view>
		<view style="margin: 60rpx 40rpx;">
			<u-button @click="showBullet.one = true" type="error" text="样式一"></u-button>
		</view>
		<view style="margin: 60rpx 40rpx;">
			<u-button @click="showBullet.two = true" type="success" text="样式二"></u-button>
		</view>
	</view>
</template>

<script>
	import ithuiBulletOne from '@/components/ithui-bullet/ithui-bullet-one';
	import ithuiBulletTwo from '@/components/ithui-bullet/ithui-bullet-two';

	export default {
		components: {
			ithuiBulletOne,
			ithuiBulletTwo
		},
		data() {
			return {
				showBullet: {
					one: false,
					two: false
				},
				content: {
					one: `<p><span style="font-size: 14px;"><strong>1.活动对象</strong></span></p><p><span style="font-size: 14px;">某APP用户</span></p><p><span style="font-size: 14px;"><strong>2.活动时间</strong></span></p><p><span style="font-size: 14px;">2023年1月1日-2023年12月31日</span></p><p><span style="font-size: 14px;"><strong>3.签到说明</strong></span></p><p><span style="font-size: 14px;">a）登录某APP/某小程序，进入积分中心活动页面即可完成每日签到，并获得签到奖励3积分。连续签到第7天、第14天、第28天可获得连签礼。</span></p><p><span style="font-size: 14px;">b）通过某APP积分中心获得的积分仅限在本活动或关联活动页面内使用，可用于奖品兑换和抽奖。</span></p><p><span style="font-size: 14px;">c）积分有效期：用户领取但未使用的积分将在每个自然年底过期，某APP将会对过期积分进行作废处理。2023年的积分将在12月31日23:59:59过期，过期后未使用的积分将自动失效，请在积分有效期内尽快使用。</span></p><p><span style="font-size: 14px;">d）积分说明：用户通过任务积累的积分需手动领取，每周（周日0:00-周六24:00）未及时领取的积分将于次周周日24:00失效，以下任务除外：成功邀请1名新用户，此类任务的积分领取有效期至每月最后一天24:00。</span></p><p><span style="font-size: 14px;">e）因活动参与用户较多，积分可能存在延迟到账情况，请耐心等待。</span></p><p><span style="font-size: 14px;"><strong>4.福利专区兑换说明</strong></span></p><p><span style="font-size: 14px;">a）根据市场变化，积分中心可调整积分累计规则、更换奖品清单或调整兑换所需积分以及本规则其他内容，相关内容以某APP积分中心规则最新公示为准，可供兑换奖品种类及积分兑换值以兑换当日积分中心福利专区公布内容为准。</span></p><p><span style="font-size: 14px;">b）用户使用积分兑奖前，请仔细阅读奖品详情，确认兑换后，用户不可要求主办方取消兑奖及退回积分。</span></p><p><span style="font-size: 14px;"><strong>5.奖品说明</strong></span></p><p><span style="font-size: 14px;">a）活动奖品、兑奖规则、兑奖所需积分请以用户登录活动后的的页面信息为准，数量有限，派完即止，奖品与兑换所需积分将进行不定期调整，请以活动页信息为准。</span></p><p><br></p><p><span style="font-size: 14px;">*本活动与苹果公司无关，苹果公司不是赞助商，并且不会以任何形式参与。</span></p>`,
					two: `<p><strong>操作指引</strong></p><p><span style="font-size: 14px;">1.点击下方按钮</span><span style="color: rgb(225, 60, 57); font-size: 14px;">【去完成】</span><span style="font-size: 14px;">；</span></p><p><span style="font-size: 14px;">2.发布动态所在的圈子人数≥2；动态内容需带话题“#五一 ”；动态照片数量≥5；</span></p><p><span style="font-size: 14px;">3.若未加入圈子，可先创建或加入一个圈子再完成任务。</span></p><p><br></p><p><strong>奖品领取</strong></p><p><span style="font-size: 14px;">完成任务后，点击</span><span style="color: rgb(115, 209, 61); font-size: 14px;">积分中心</span><span style="font-size: 14px;">顶部待领取积分即可获得奖励。</span></p><p><br></p><p><br></p>`
				}
			}
		},
		onLoad() {},
		methods: {
			handleConfirm(e) {
				uni.showToast({
					title: `点击了样式${e}的确定`,
					duration: 2000,
					icon: 'none'
				});
			},
			handleCancel(e) {
				uni.showToast({
					title: `点击了样式${e}的取消`,
					duration: 2000,
					icon: 'none'
				});
			},
			handleClose(e) {
				uni.showToast({
					title: `点击了样式${e}的遮罩`,
					duration: 2000,
					icon: 'none'
				});
			}
		}
	}
</script>

<style>
	page {
		background-color: #fff;
	}
</style>

<style lang="scss" scoped>
	.ithui {
		&-content {}
	}
</style>