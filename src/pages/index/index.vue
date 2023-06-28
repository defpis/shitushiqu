<template>
	<view class="container">
		<view class="region-select">
			<text>选择你想去旅行的地区</text>

			<view class="region-list">
				<view v-for="item of regions">
					<text>{{ item.regionName }}</text>
					<image :src="item.coverImgUrl"></image>
				</view>
			</view>
		</view>

		<view class="region-submit">
			<button class="btn-top">
				<image src="../../static/icons/arrow-up.svg"></image>
				返回首页
			</button>

			<view class='tips'>
				<text>不好意思，人手有限，目前只有以上地区数据</text>
				<text>我们正在哼哧哼哧地挑选更多好看的地区</text>

				<image src="../../static/images/illustration/work-hard.png"></image>
			</view>

			<view>
				<button @click="open" type="primary" class="btn-bottom">告诉我们你想去的地区</button>
				<uni-popup ref="popup" type="bottom" background-color="#fff">
					<view class="form">
						<uni-forms label-position="top">
							<uni-forms-item label="推荐景点">
								<uni-easyinput type="text" />
							</uni-forms-item>
							<uni-forms-item label="推荐理由">
								<uni-easyinput type="textarea" />
							</uni-forms-item>
							<view class="action">
								<button type="primary">提交</button>
								<button @click="close">取消</button>
							</view>
						</uni-forms>
					</view>
				</uni-popup>
			</view>
		</view>

	</view>
</template>

<script>

import Vue from 'vue';

export default Vue.extend({
	data() {
		return {
			regions: [
				{
					regionName: '新疆',
					coverImgUrl: '../../static/images/cover/example.jpg'
				},
				{
					regionName: '川西',
					coverImgUrl: '../../static/images/cover/example.jpg'
				},
				{
					regionName: '西藏',
					coverImgUrl: '../../static/images/cover/example.jpg'
				}
			],
		}
	},
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
.region-list {
	>view {
		margin-block-start: 20px;
		height: 240px;
		position: relative;
		overflow: hidden;

		&:last-child {
			margin-block-end: 40px;
		}
	}

	text {
		font-weight: 900;
		font-size: 64px;
		color: white;
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
	}

	image {
		width: 100%;
		border-radius: 12px;
	}
}

.region-submit {
	.btn-top {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		background-color: white;
		border: 0.5px solid #dedede;
		font-weight: 400;
		font-size: 16px;
		width: 160px;
		margin-block-start: 40px;
		border-radius: 32px;

		>image {
			width: 20px;
			height: 20px;
			margin-inline-end: 4px;
		}
	}

	.tips {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-block-start: 40px;

		>text {
			margin: 8px 0;
			color: #666;
			font-size: 16px;
		}

		>image {
			width: 100%;
			margin-block-start: 20px;
		}
	}

	.btn-bottom {
		margin-block-start: 40px;
		margin-block-end: 40px;
	}

	.form {
		padding: 20px;

		.action {
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
}
</style>
