<template>
  <view class="page-container">
    <view class="header-container">
      <view class="left" @click="toBack"><text class="iconfont icon-back"></text></view>
      <view class="center">报修列表</view>
      <view class="right">
        <text class="iconfont icon-jia" @click="toPushPage"></text>
      </view>
    </view>
    <view class="main-container">
      <view class="repair-list-container">
        <view class="repair-item-container" @click="toDetailPage">
          <view class="state-bar"></view>
          <view class="content">
            <view class="title">周舟船</view>
            <view class="message">西环北路路口第37号路灯出现故障</view>
            <view class="time">2020.07.12 12:12:32</view>
          </view>
        </view>
        <view class="repair-item-container" @click="toDetailPage">
          <view class="state-bar"></view>
          <view class="content">
            <view class="title">周舟船</view>
            <view class="message">西环北路路口第37号路灯出现故障</view>
            <view class="time">2020.07.12 12:12:32</view>
          </view>
        </view>
        <view class="repair-item-container" @click="toDetailPage">
          <view class="state-bar"></view>
          <view class="content">
            <view class="title">周舟船</view>
            <view class="message">西环北路路口第37号路灯出现故障</view>
            <view class="time">2020.07.12 12:12:32</view>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  methods: {
    toPushPage() {
      uni.navigateTo({
        url: '/pages/reportForRepair/push',
      });
    },
    toDetailPage() {
      uni.navigateTo({
        url: '/pages/reportForRepair/detail',
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
  background-color: #f3f3f3;
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

.repair-list-container {
  padding: 15px;
  display: flex;
  flex-direction: column;
}

.repair-item-container {
  margin-bottom: 15px;
  display: flex;
  flex-direction: row;
  border-radius: 8px;
  box-shadow: 0px 0px 15px #ccc;
  overflow: hidden;
}

.repair-item-container .state-bar {
  width: 15px;
  min-height: 100px;
  background-color: #aef9c5;
  flex-shrink: 0;
}

.repair-item-container .content {
  flex-grow: 1;
  padding: 15px;
}

.repair-item-container .content .title {
  font-size: 16px;
  color: #333;
  font-weight: bold;
}

.repair-item-container .content .message {
  font-size: 14px;
  margin-top: 5px;
}

.repair-item-container .content .time {
  font-size: 14px;
  color: #999;
  margin-top: 5px;
}
</style>