<template>
  <view>
    <view class="container">
      <text class="name">景点名称</text>

      <view class="travel-date-range">
        <text>推荐旅行时间：</text>
        <text class="date-range">2020.01.01 - 2020.12.01</text>
      </view>

      <text class="desc">一段简单关键信息的景点描述文本一段简单关键信息的景点描述文本一段简单关键信息的景点描述文本</text>

      <view class="album" v-for="(item, index) in albums" :key="index" @tap="preview(item)">
        <view class="album-date">
          <text>照片拍摄于：2020.01.01</text>
        </view>
        <image mode='aspectFill' src="../../static/images/spot/big-cover.png"></image>
      </view>
    </view>

    <view class="action">
      <button @tap="toggle">
        <image mode='aspectFill' :src="star ? '../../static/icons/star.svg' : '../../static/icons/star-2.svg'"></image>
        <text>取消收藏</text>
      </button>
      <button>
        <image mode='aspectFill' src="../../static/icons/export-2.svg"></image>
        <text>微信分享</text>
      </button>
    </view>
  </view>
</template>

<script>
import { range } from 'lodash';
import Vue from 'vue';

export default Vue.extend({
  created() {
    uni.setNavigationBarTitle({
      title: '景点名称'
    })
  },
  data() {
    return {
      star: true,
      albums: range(10).map((i) => ({
        id: i,
      }))
    }
  },
  methods: {
    toggle() {
      this.star = !this.star;
    },
    preview(item) {
      uni.navigateTo({
        url: '/pages/spot/preview',
      })
    },
  }
})
</script>

<style lang="scss">
.action {
  padding: 0 24px;
  box-sizing: border-box;
  position: fixed;
  bottom: 20px;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;

  >button {
    padding: 16px;
    border-radius: 28px;
    border: 1px solid rgba(0, 0, 0, 0.10);
    background: #FFF;

    flex: 1;
    margin-inline-start: 20px;
    display: flex;
    align-items: center;
    justify-content: center;

    color: #000;
    font-size: 16px;
    line-height: 16px;
    font-weight: 500;

    &:first-child {
      margin-inline-start: 0;
    }

    >image {
      width: 20px;
      height: 20px;
      margin-inline-end: 12px;
    }
  }
}

.album {
  margin-block-start: 16px;
  position: relative;

  &:first-child {
    margin-block-start: 20px;
  }

  >.album-date {
    position: absolute;
    top: 12px;
    left: 12px;

    padding: 4px 10px;
    border-radius: 4px;
    background: #000;

    >text {
      color: #FFF;
      text-align: center;
      font-size: 14px;
      font-weight: 500;
    }
  }

  >image {
    width: 100%;
    border-radius: 12px;
  }
}

.container {
  padding: 24px 24px 96px;
}

.name {
  color: #333;
  font-size: 20px;
  font-weight: 500;
}

.travel-date-range {
  margin-block-start: 8px;
  color: #666;
  font-size: 14px;
  font-weight: 400;

  .date-range {
    color: #0075FF;
    font-weight: 600;
  }
}

.desc {
  margin-block-start: 8px;
  color: #333;
  font-size: 14px;
  font-weight: 400;
}
</style>