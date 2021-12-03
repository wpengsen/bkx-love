<!-- 微信授权登录全程代码实现 -->
<template>
	<view>
		<view>
			<view class="u-page__item">
				<u-navbar leftText="返回" title="个人中心" :safeAreaInsetTop="false">
					<view class="u-nav-slot" slot="left">
						<u-icon name="arrow-left" size="19"></u-icon>
						<u-line direction="column" :hairline="false" length="16" margin="0 8px"></u-line>
						<u-icon name="home" size="20"></u-icon>
					</view>
				</u-navbar>
			</view>
			<u-gap height="50"></u-gap>
		</view>
		<view class="u-demo-block">
			<text class="u-demo-block__title">邀请函</text>
			<!-- <view class="u-demo-block__content">
				<view class="u-page__image-item">
					<u--image :showLoading="true" src="" width="80px" height="80px"></u--image>
				</view>
			</view> -->
		</view>
		<button open-type="getUserInfo" @tap="getUserInfo" size="mini"> 点我登录 </button>
		<view>关键词拦截</view>
		<view>可以添加表情</view>
		<view>可以添加表情</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userList: [],
			}
		},
		onLoad() {
			uni.showToast({
				title: "小可爱我爱你哦！",
				icon: "none"
			})
		},
		methods: {
			login() {
				// 获取用户信息
				uni.getUserInfo({
					provider: 'weixin',
					success: function(infoRes) {
						uni.showToast({
							title: "昵称" + infoRes.userInfo.nickName
						})
						console.log('用户昵称为：' + infoRes.userInfo.nickName);
					}
				});
			},
			getUserInfo() {
				uni.getUserProfile({
					desc: "登录",
					lang: "zh_CN",
					success: (res) => {
						uni.showToast({
							title: "您的昵称是：" + res.userInfo.nickName,
							icon: "none"
						})
						console.info(res);
						console.info(res.userInfo);
					}
				})
			}
		},
	}
</script>
<style lang="scss">
	.u-page {
		padding: 0;

		&__item {

			&__title {
				color: $u-tips-color;
				background-color: $u-bg-color;
				padding: 15px;
				font-size: 15px;

				&__slot-title {
					color: $u-primary;
					font-size: 14px;
				}
			}
		}
	}

	.u-nav-slot {
		@include flex;
		align-items: center;
		justify-content: space-between;
		border-width: 0.5px;
		border-radius: 100px;
		border-color: $u-border-color;
		padding: 3px 7px;
		opacity: 0.8;
	}
</style>
