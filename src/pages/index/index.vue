<template>
	<view class="container">
		<view class="region-select">
			<text>选择你想去旅行的地区</text>

			<view class="region-list">
				<view v-for="region of regions">
					<text>{{ region.regionName }}</text>
					<image :src="region.coverImgUrl"></image>
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

			<view id="form-popup" v-if="showForm">
				<mp-form>
					<mp-cell title="姓名" prop="userName">
						<input placeholder="请输入姓名" />
					</mp-cell>
				</mp-form>
			</view>

			<button type="primary" class="btn-bottom" @tap="toggleForm">告诉我们你想去的地区</button>
		</view>

	</view>
</template>

<script lang="ts">
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
			showForm: false
		}
	},
	methods: {
		toggleForm() {
			this.showForm = !this.showForm;
		}
	}
});
</script>

<style>
.region-list>view {
	margin-block-start: 20px;
	height: 240px;
	position: relative;
	overflow: hidden;
}

.region-list>view:last-child {
	margin-block-end: 40px;
}

.region-list image {
	width: 100%;
	border-radius: 12px;
}

.region-list text {
	font-weight: 900;
	font-size: 64px;
	color: white;
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%, -50%);
}

.region-submit .btn-top {
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
}

.region-submit .btn-top>image {
	width: 20px;
	height: 20px;
	margin-inline-end: 4px;
}

.region-submit .tips {
	display: flex;
	flex-direction: column;
	align-items: center;
	margin-block-start: 40px;
}

.region-submit .tips>text {
	margin: 8px 0;
	color: #666;
	font-size: 16px;
}

.region-submit .tips>image {
	width: 100%;
	margin-block-start: 20px;
}

.region-submit .btn-bottom {
	margin-block-start: 40px;
	margin-block-end: 40px;
}

#form-popup {
	position: fixed;
	left: 0;
	bottom: 0;
	width: 100%;
	background: #fff;
	z-index: 99;
	animation: showPopup 0.3s linear;
}

@keyframes showPopup {
	from {
		transform: translateY(100%);
	}

	to {
		transform: translateY(0);
	}
}
</style>
