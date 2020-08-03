<template>
  <view class="page-container">
    <view class="scrollPage">
      <img
        src="~@/static/index_imgs/img2.png"
        class="png"
        style="width:100%; height: 148px"
      />
      <!--banner-->
      <view style="margin-top: -150px;padding: 0px 15px;">
        <view class="header-container">
          <view class="left"><text class="iconfont icon-dingwei1"></text> 杭州</view>
          <view class="center">首页</view>
          <view class="right">晴/30℃</view>
        </view>
        <view style="text-align: center;">
          <img
            src="~@/static/index_imgs/banner.jpeg"
            style="width:100%;border-radius:8rpx;"
          />
        </view>
      </view>
      <!--通知-->
      <view class="new_frame">
        <view class="icon">
          <img src="~@/static/index_imgs/new.png" style="width:28px;height:28px" />
        </view>
        <view style="flex-grow: 1; display: flex; justify-content: center; align-items: center; flex-direction: column;">
          <view style="color: #333; font-size: 14px;white-space: pre; text-overflow: ellipsis;">· 第四届江苏省中小学生比赛开始拉</view>
          <view style="color: #333; font-size: 14px;white-space: pre;text-overflow: ellipsis;">· 阳坡湖赏花节|4月20日 - 5月20日</view>
        </view>
      </view>
      <!--列表-->
      <view style="margin-top:20rpx">
        <view class="navline">
          <scroll-view scroll-x class="bg-white nav">
            <view
              class="cu-item"
              :class="{cur: TabCur === index}"
              v-for="(item, index) in list"
              :key="index"
              @click="tabSelect(index)"
            >
              <text class="batchSelect">{{ item }}</text>
            </view>
          </scroll-view>
        </view>
      </view>

      <view v-if="TabCur == 0">
        <view class="order-container" >
          <view class="image-container">
            <img
              src="~@/static/index_imgs/img1.png"
              style="width:200rpx;height:150rpx;border-radius:8rpx"
            />
          </view>
          <view class="content-container">
            <view class="title">汀州园游船票</view>
            <view class="user">用户:张淮安</view>
            <view class="time">下单时间:2020.09.10</view>
          </view>
        </view>

        <view class="order-container" >
          <view class="image-container">
            <img
              src="~@/static/index_imgs/img1.png"
              style="width:200rpx;height:150rpx;border-radius:8rpx"
            />
          </view>
          <view class="content-container">
            <view class="title">汀州园游船票</view>
            <view class="user">用户:张淮安</view>
            <view class="time">下单时间:2020.09.10</view>
          </view>
        </view>

        <view class="order-container" >
          <view class="image-container">
            <img
              src="~@/static/index_imgs/img1.png"
              style="width:200rpx;height:150rpx;border-radius:8rpx"
            />
          </view>
          <view class="content-container">
            <view class="title">汀州园游船票</view>
            <view class="user">用户:张淮安</view>
            <view class="time">下单时间:2020.09.10</view>
          </view>
        </view>
      </view>
      <view v-if="TabCur == 1">
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
    <view class="tabs-container">
      <view class="tab" @click="changePage('home')">
        <img v-if="pageIndex === 'home'" src="~@/static/index_slices/icon_home_1@3x.png" alt />
        <img v-else src="~@/static/mine_slices/icon_home@3x.png" alt />
        <text :class="pageIndex === 'home' ? 'active' : ''">首页</text>
      </view>
      <view class="tab" @click="changePage('find')">
        <img v-if="pageIndex === 'find'" src="~@/static/index_slices/icon_find_1@3x.png" alt="">
        <img v-else src="~@/static/index_slices/icon_find@3x.png" alt="">
        <text :class="pageIndex === 'find' ? 'active' : ''">设备管理</text>
      </view>
      <view class="tab" @click="changePage('order')">
        <img v-if="pageIndex === 'order'" src="~@/static/order_slices/icon_order_1@3x.png" alt />
        <img v-else src="~@/static/index_slices/icon_order@3x.png" alt />
        <text :class="pageIndex === 'order' ? 'active' : ''">报修</text>
      </view>
      <view class="tab" @click="changePage('mine')">
        <img v-if="pageIndex === 'mine'" src="~@/static/mine_slices/icon_mine_1@3x.png" alt />
        <img v-else src="~@/static/index_slices/icon_mine@3x.png" alt />
        <text :class="pageIndex === 'mine' ? 'active' : ''">我的</text>
      </view>
    </view>
  </view>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data() {
    return {
      pageIndex: "home",
      list: ["游园订单", "报修列表"],
      TabCur: 0,
      scrollLeft: 0,
    };
  },
  onLoad() {},
  methods: {
    changePage(value: string) {
      // this.pageIndex = value;
      if (value === "order") {
        uni.navigateTo({
          url: "/pages/reportForRepair/list",
        });
      }
      if (value === "mine") {
        uni.navigateTo({
          url: "/pages/index/mine",
        });
      }
      if (value === "find") {
        uni.navigateTo({
          url: "/pages/index/device",
        });
      }
    },
    tabSelect(id: any) {
      this.TabCur = id;
      // this.scrollLeft = (id - 1) * 60;
      // if (id === 1) {
      //   uni.navigateTo({
      //     url: "/pages/reportForRepair/list",
      //   });
      // }
    },
    toDetailPage() {
      uni.navigateTo({
        url: '/pages/reportForRepair/detail',
      });
    }
  },
});
</script>

<style>
.page-container {
  height: 100vh;
  background-color: white;
  display: flex;
  flex-direction: column;
}

.scrollPage {
  flex-grow: 1;
  overflow: auto;
}

.header-container {
  color: #FFFFFF;
  height: 18px;
  padding: 15px;
  flex-shrink: 0;
  display: flex;
  margin-bottom: 10px;
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

.new_frame {
  height: 90rpx;
  margin: 0 15px;
  margin-top: 20rpx;
  background-color: white;
  box-shadow: 1px 3px 6px 1px rgb(232,232,232);
  border-radius: 8rpx;
  display: flex;
  padding: 15px;
}

.new_frame .icon {
  width: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-shrink: 0;
}

.navline {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  background-color: white;
}
.nav {
  white-space: nowrap;
}

.nav .cu-item {
  height: 90rpx;
  display: inline-block;
  line-height: 90rpx;
  margin: 0 10rpx;
  padding: 0 20rpx;
}

.batchSelect {
  color: #9a9a9a;
  font-size: 15px;
  font-weight: bold;
  padding-bottom: 5px;
}

.nav .cu-item.cur .batchSelect {
  color: #333333;
  border-bottom: 2px solid #129efb;
}

.order-container {
  display: flex;
  padding: 15px;
}

.order-container .image-container {
  width: 100px;
  height: 75px;
  margin-right: 15px;
}

.order-container .content-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.order-container .content-container .title {
  font-size: 16px;
  color: #333333;
}

.order-container .content-container .user {
  color: #9a9a9a;
  font-size: 14px;
}

.order-container .content-container .time {
  color: #9a9a9a;
  font-size: 14px;
}

.tabs-container {
  height: 40px;
  flex-shrink: 0;
  padding: 5px 0px;
  background: #ffffff;
  box-shadow: 0px 12px 26px 3px rgba(0, 0, 0, 0.34);
  display: flex;
}

.tabs-container .tab {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.tabs-container .tab img {
  width: 20px;
}

.tabs-container .tab text {
  color: #9a9a9a;
  font-size: 12px;
}

.tabs-container .tab text.active {
  color: #333333;
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
