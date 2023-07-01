<template>
	<view class="container">
		<uni-swipe-action class="content">
			<uni-swipe-action-item class="spot-wrapper" v-for="(item, index) in collections" :key="index">
				<view style="padding: 0 20px;">
					<view class="spot-card" @longtap="longtap" @tap="detail(item)">
						<image mode='aspectFill' :src="item.coverUrl"></image>
						<view>
							<view class="spot-title">
								<text>{{ item.spotName }}</text>
								<uni-tag :text="item.regionName" :inverted="true" type="primary" />
							</view>
							<view class="spot-info">
								<text>推荐旅行时间：</text>
								<text class="time">{{ item.recommendedTime }}</text>
							</view>
						</view>
					</view>
				</view>

				<template v-slot:right>
					<button class="spot-remove" @tap="remove(index)">取消收藏</button>
				</template>
			</uni-swipe-action-item>
		</uni-swipe-action>

		<uni-popup ref="popup" type="bottom" :safeArea="false" background-color="#fff">
			<view class="action">
				<button>分享到微信</button>
				<button>取消收藏</button>
				<button @tap="close">取消</button>
			</view>
		</uni-popup>
	</view>
</template>

<script>
import Vue from 'vue';
import { range } from 'lodash'

export default Vue.extend({
	data() {
		return {
			collections: [
				...range(10).map((i) => ({
					coverUrl: '../../static/images/spot/mini-cover.png',
					spotName: '景点名称' + i,
					regionName: '区域名称',
					recommendedTime: '2020.01.01'
				}))
			],
			timer: -1,
		}
	},
	methods: {
		detail(item) {
			uni.navigateTo({
				url: '/pages/spot/spot',
			})
		},
		remove(index) {
			this.collections.splice(index, 1)
		},
		open() {
			this.$refs.popup.open('bottom')
		},
		close() {
			this.$refs.popup.close('bottom')
		},
		longtap() {
			this.open();
		}
	}
});
</script>

<style lang="scss">
.action {
	>button {
		border-radius: 0;
	}

	>button::after {
		border-radius: 0;
	}
}

.content {
	padding: 20px 0;

	>view {
		display: flex;
		flex-direction: column;
	}
}

.spot-wrapper {
	box-shadow: 1px 1px 10px 0px rgba(0, 0, 0, 0.01);

	margin-block-start: 20px;

	&:first-child {
		margin-block-start: 0;
	}
}

.spot-remove {
	margin-inline-end: 20px;
	border-radius: 24px;
	background: #FF2E00;
	box-shadow: 1px 1px 10px 0px rgba(0, 0, 0, 0.01);
	display: flex;
	align-items: center;
	color: white;
	padding: 18px;
	font-size: 14px;
}

.spot-card {
	border-radius: 24px;
	background-color: #fff;
	padding: 16px;
	flex: 1;
	display: flex;
	flex-direction: row;

	>image {
		width: 100px;
		height: 100px;
	}

	>view {
		margin-inline-start: 20px;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		padding-block-start: 20px;
		padding-block-end: 20px;
	}

	.spot-title {
		>text {
			font-size: 16px;
			font-weight: 500;
			color: #333;
			margin-inline-end: 8px;
		}
	}

	.spot-info {
		font-size: 14px;

		>.time {
			color: #0075FF;
			font-weight: 600;
		}
	}
}
</style>
