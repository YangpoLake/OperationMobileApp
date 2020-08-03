<template>
  <view class="alarm-container">
    <view class="header-container">
      <view class="left" @click="toBack"><text class="iconfont icon-back"></text></view>
      <view class="center">一键报警</view>
      <view class="right"></view>
    </view>
    <view class="main-container">
      <view class="alarm-btn"></view>
      <view class="alarm-tip">
        <text>长按向后台发送警报</text>
      </view>
    </view>
  </view>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  
})
</script>
<style scoped>
.alarm-container {
  width: 100vw;
  height: 100vh;
  background-color: #f3f3f3;
  display: flex;
  flex-direction: column;
}

.header-container {
  color: #333333;
  height: 24px;
  padding: 15px;
  flex-shrink: 0;
  display: flex;
  background-color: #FFFFFF;
}

.header-container .left,
.header-container .right {
  font-size: 16px;
  width: 100px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
}

.header-container .center {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.main-container {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.alarm-btn {
  margin: 0px 30px;
  flex-grow: 1;
  background: url("~@/static/other_slices/alarm-btn.png") no-repeat center;
  background-size: contain;
}

.alarm-tip {
  height: 50px;
  color: #999999;
  font-size: 12px;
  flex-shrink: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>