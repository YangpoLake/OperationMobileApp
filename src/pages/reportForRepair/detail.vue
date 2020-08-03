<template>
  <view class="page-container">
    <view class="header-container">
      <view class="left" @click="toBack"><text class="iconfont icon-back"></text></view>
      <view class="center">报修详情</view>
      <view class="right"></view>
    </view>
    <view class="main-container">
      <view class="form-container">
        <view class="form-item-label">报修描述</view>
        <view class="form-item-content">
          <text>西环北路路口第37号路灯出现故障</text>
        </view>
        <view class="form-item-content image-list-container">
          <view class="image-container" v-for="item in [0, 1, 2]" :key="item">
            <img src="~@/static/report_for_repair_imgs/image.png" alt="">
          </view>
        </view>
        <view class="form-item-content image-list-container">
          <view class="image-container" v-for="item in [0, 1, 2]" :key="item">
            <img src="~@/static/report_for_repair_imgs/image.png" alt="">
          </view>
        </view>
        <view class="form-action-content">
          <button class="submit-btn" @click="toFeedbackPage">我来解决</button>
        </view>
      </view>
    </view>
  </view>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  methods: {
    toFeedbackPage() {
      uni.navigateTo({
        url: '/pages/reportForRepair/feedback',
      });
    },
    toBack() {
      uni.navigateBack({ delta: 1 })
    }
  }
})
</script>
<style scoped>
.page-container {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.header-container {
  color: #333333;
  height: 24px;
  padding: 15px;
  flex-shrink: 0;
  display: flex;
}

.header-container .left,
.header-container .right {
  font-size: 16px;
  width: 100px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
}

.header-container .right {
  flex-direction: row-reverse;
}

.header-container .right .iconfont {
  font-size: 22px;
}

.header-container .center {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.main-container {
  flex-grow: 1;
  overflow: auto;
}

.form-container {
  padding: 15px;
}

.form-container .form-item-label {
  font-size: 16px;
  color: #333333;
}

.form-container .form-item-content {
  margin-top: 15px;
  display: flex;
}

.form-item-content text {
  color: #999;
  font-size: 16px;
}

.image-list-container {
  display: flex;
  justify-content: space-between;
}

.form-container textarea {
  flex-grow: 1;
  border-radius: 8px;
  padding: 5px;
  background-color: #f4f7f7;
}

.image-container {
  width: 30%;
  height: 100px;
  border-radius: 8px;
  overflow: hidden;
  border-radius: 8px;
  background-color: #f4f7f7;
}

.image-container img {
  width: 100%;
  height: 100%;
}

.form-action-content {
  margin-top: 15px;
}

.submit-btn {
  color: #FFF;
  background-color: #5ed17e;
}
</style>