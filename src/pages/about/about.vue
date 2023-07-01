<template>
	<view class="container">
		<view class="user-info">
			<view class="user">
				<image mode='aspectFill' src="../../static/images/avatar/login-user.png"></image>
				<text>AbnerTang</text>
			</view>
			<view class="login">
				<text>已通过微信登录</text>
			</view>
		</view>

		<view class="logo">
			<image mode='aspectFill' src="../../static/images/text/journey.png"></image>
		</view>

		<view class="tips">
			<text>每个地方都有它最美的时间。</text>
			<text>在你想要旅行时，时途希望帮你找到那时那刻最美的地方，让你在指定时间遇见最美的景色。</text>
		</view>

		<view class="action">
			<button>
				<image mode='aspectFill' src="../../static/icons/export.svg"></image>
				<text>分享给你的朋友们</text>
			</button>
			<button>
				<image mode='aspectFill' style="width: 48px; height: 48px;" src="../../static/icons/drink.svg"></image>
				<text>赏一杯奶茶 (￥10)</text>
			</button>
			<button @tap="open">
				<image mode='aspectFill' src="../../static/icons/edit.svg"></image>
				<text>给我们反馈</text>
			</button>

			<uni-popup ref="popup" type="bottom" :safeArea="false" background-color="#fff">
				<view class="form">
					<uni-forms label-position="top">
						<uni-forms-item label="反馈内容">
							<uni-easyinput type="textarea" />
						</uni-forms-item>
						<view class="form-action">
							<button @tap="close">取消</button>
							<button type="primary">提交</button>
						</view>
					</uni-forms>
				</view>
			</uni-popup>
		</view>
	</view>
</template>

<script>
import Vue from 'vue';

export default Vue.extend({
	methods: {
		open() {
			this.$refs.popup.open('bottom')
		},
		close() {
			this.$refs.popup.close('bottom')
		}
	}
});
</script>

<style lang="scss">
.form {
	padding: 20px;

	.form-action {
		display: flex;
		flex-direction: row;
		justify-content: space-between;

		>button {
			flex: 1;
			margin-inline-start: 20px;

			&:first-child {
				margin-inline-start: 0;
			}
		}
	}
}

.container {
	padding: 20px;
}

.action {
	>button {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-block-start: 20px;
		padding: 14px;
	}

	image {
		width: 32px;
		height: 32px;
	}
}

.tips {
	display: flex;
	flex-direction: column;
	align-items: center;

	color: #666;
	text-align: center;
	font-size: 16px;
	font-style: normal;
	font-weight: 400;
}

.logo {
	margin: 80px auto 20px;

	>image {
		width: 228px;
		height: 62px;
	}
}

.user-info {
	padding: 20px;
	display: flex;
	justify-content: space-between;
	border-radius: 12px;
	background: #F2F2F2;

	>view {
		display: flex;
		align-items: center;
	}

	.user {
		>image {
			width: 40px;
			height: 40px;
			border-radius: 40px;
			border: 1px solid rgba(0, 0, 0, 0.10);
		}

		>text {
			margin-inline-start: 10px;
			color: #333;
			font-size: 16px;
			font-style: normal;
			font-weight: 500;
		}
	}

	.login {
		color: #666;
		font-size: 16px;
		font-style: normal;
		font-weight: 400;
	}
}
</style>
