<template>
  <view class="container">
    <view class="noop"></view>

    <swiper class="content">
      <swiper-item v-for="(item, index) in pictures" :key="index">
        <view class="preview">
          <image mode='widthFix' :src="item.url"></image>
          <view class="info">
            <view>
              <image src="../../static/icons/camera.svg"></image>
              <text>拍摄时间：2020.01.01</text>
            </view>
            <text>{{ index }}/{{ pictures.length }}</text>
          </view>
        </view>
      </swiper-item>
    </swiper>

    <view class="copyright">
      <text>图像可能受版权保护</text>
      <text>|</text>
      <text class="username">username</text>
      <image src="../../static/images/avatar/image-uploader.png"></image>
    </view>
  </view>
</template>

<script>

import { range } from 'lodash';
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      pictures: range(10).map((i) => ({
        url: '../../static/images/spot/preview.png'
      })),
      x: 0,
      y: 0,
    }
  },
  methods: {
    change: (ev) => {
      console.log(ev);
    }
  }
})

</script>

<style lang="scss">
.copyright {
  padding: 0 24px;
  width: 100%;
  box-sizing: border-box;
  display: flex;
  flex-direction: row-reverse;
  align-items: center;

  color: rgba(255, 255, 255, 0.60);
  font-size: 12px;
  font-weight: 500;

  text {
    margin-inline-start: 8px;
  }

  image {
    width: 24px;
    height: 24px;
  }

  .username {
    color: rgba(255, 255, 255, 0.80);
    font-size: 14px;
  }
}

.preview {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  >image {
    width: 100%;
  }

  .info {
    padding: 14px 24px;
    width: 100%;
    box-sizing: border-box;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;

    view {
      display: flex;
      align-items: center;
    }

    image {
      width: 16px;
      height: 16px;
      margin-inline-end: 8px;
    }
  }
}

.container {
  padding: 24px 0 48px;

  flex-direction: column;
  justify-content: space-between;
  align-items: center;

  background-color: black;
  color: white;

  .content {
    width: 100%;
    flex: 1;
    overflow: hidden;
  }
}
</style>