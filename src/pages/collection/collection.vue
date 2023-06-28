<template>
	<view class="container">

		<view class="spot-wrapper" @touchstart="onStart" @touchend="onEnd" @touchmove="onMove" v-for="item of collections">
			<view>
				<view class="spot-card">
					<image :src="item.coverUrl"></image>
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

				<view class="spot-unstar">
					<text>取消收藏</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
import Vue from 'vue';
import { range } from 'lodash'

export default Vue.extend({
	data() {
		return {
			collections: [
				...range(10).map(() => ({
					coverUrl: '../../static/images/spot/mini-cover.png',
					spotName: '景点名称',
					regionName: '区域名称',
					recommendedTime: '2020.01.01'
				}))
			]
		}
	},
	methods: {
		onStart() {
			console.log('start')
		},
		onMove(ev) {
			console.log('move', ev)
		},
		onEnd() {
			console.log('end')
		}
	}
});
</script>

<style lang="scss">
.spot-wrapper {
	>view {
		position: relative;
		height: 132px;
		display: flex;
		flex-direction: row;
	}

	margin-block-start: 20px;

	&:first-child {
		margin-block-start: 0;

		.spot-card {
			left: -116px;
		}

		.spot-unstar {
			right: 0;
			display: flex;
		}
	}

	&:last-child {
		margin-block-end: 40px;
	}
}

.spot-unstar {
	border-radius: 24px;
	background: #FF2E00;
	box-shadow: 1px 1px 10px 0px rgba(0, 0, 0, 0.01);

	position: absolute;
	top: 0;
	right: 0;
	height: 100%;
	display: none;
	// display: flex;
	align-items: center;
	color: white;
	padding: 18px;
	box-sizing: border-box;
}

.spot-card {
	position: absolute;
	top: 0;
	left: 0;

	border-radius: 24px;
	background: #FFF;
	box-shadow: 1px 1px 10px 0px rgba(0, 0, 0, 0.01);
	width: 100%;
	box-sizing: border-box;

	height: 100%;
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
