<template>
  <view class="mine-container">
    <view class="header-container">
      <view class="header">
        <view class="left"></view>
        <view class="center">我的</view>
        <view class="right"></view>
      </view>
      <view class="mineinfo">
        <img src="~@/static/index_slices/banner@3x.png" />
        <view class="detail">
          <text>富春山居</text>
          <view>1567800998</view>
        </view>
      </view>
    </view>
    <view class="main-container">
      <view class="menu-container">
        <view class="menu-item" @click="toPushPage">
          <img class="icon-left" src="~@/static/mine_slices/icon_01@3x.png" alt />
          <view class="label">设备报修</view>
          <img class="icon-right" src="~@/static/mine_slices/icon_right@3x.png" alt />
        </view>
        <view class="menu-item" @click="toAlarmPage">
          <img class="icon-left" src="~@/static/mine_slices/icon_01@3x.png" alt />
          <view class="label">一键报警</view>
          <img class="icon-right" src="~@/static/mine_slices/icon_right@3x.png" alt />
        </view>
        <view class="menu-item" @click="scanCode">
          <img class="icon-left" src="~@/static/mine_slices/icon_01@3x.png" alt />
          <view class="label">核销扫码</view>
          <img class="icon-right" src="~@/static/mine_slices/icon_right@3x.png" alt />
        </view>
        <view class="menu-item" @click="toOrderPage">
          <img class="icon-left" src="~@/static/mine_slices/icon_01@3x.png" alt />
          <view class="label">游客订单</view>
          <img class="icon-right" src="~@/static/mine_slices/icon_right@3x.png" alt />
        </view>
        <view class="menu-item" @click="toAboutPage">
          <img class="icon-left" src="~@/static/mine_slices/icon_01@3x.png" alt />
          <view class="label">关于我们</view>
          <img class="icon-right" src="~@/static/mine_slices/icon_right@3x.png" alt />
        </view>
      </view>
    </view>
    <view class="footer-container">
      <view class="tabs-container">
        <view class="tab" @click="changePage('home')">
          <img v-if="pageIndex === 'home'" src="~@/static/index_slices/icon_home_1@3x.png" alt />
          <img v-else src="~@/static/mine_slices/icon_home@3x.png" alt />
          <text :class="pageIndex === 'home' ? 'active' : ''">首页</text>
        </view>
        <view class="tab" @click="changePage('find')">
          <img v-if="pageIndex === 'find'" src="~@/static/index_slices/icon_find_1@3x.png" alt />
          <img v-else src="~@/static/index_slices/icon_find@3x.png" alt />
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
  </view>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data() {
    return {
      pageIndex: "mine",
    };
  },
  methods: {
    changePage(value: string) {
      // this.pageIndex = value;
      if (value === "order") {
        uni.navigateTo({
          url: "/pages/reportForRepair/list",
        });
      }
      if (value === "home") {
        uni.navigateTo({
          url: "/pages/index/index",
        });
      }
      if (value === "find") {
        uni.navigateTo({
          url: "/pages/index/device",
        });
      }
    },
    toPushPage() {
      uni.navigateTo({
        url: "/pages/reportForRepair/push",
      });
    },
    toMobileCallPage() {
      location.href = "tel:17621958573";
    },
    scanCode() {
      uni.scanCode({
        success: function (res) {
          console.log(JSON.stringify(res.result));
        },
      });
    },
    toAboutPage() {
      uni.navigateTo({
        url: "/pages/other/about"
      });
    },
    toOrderPage() {
      uni.navigateTo({
        url: "/pages/order/index"
      });
    },
    toAlarmPage() {
      uni.navigateTo({
        url: "/pages/other/alarm"
      });
    }
  },
});
</script>

<style scoped>
.mine-container {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.header-container {
  /* background: url("~@/static/mine_slices/bg@3x.png") no-repeat center; */
  background-color: #129efb;
  background-size: cover;
  display: flex;
  flex-direction: column;
}

.header-container .header {
  color: #fff;
  height: 24px;
  padding: 15px;
  flex-shrink: 0;
  display: flex;
}

.header-container .header .left,
.header-container .header .right {
  font-size: 16px;
  width: 100px;
  flex-shrink: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.header-container .header .center {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.header-container .mineinfo {
  display: flex;
  padding: 15px;
  padding-bottom: 48px;
}

.header-container .mineinfo img {
  width: 60px;
  height: 60px;
  border-radius: 30px;
}

.header-container .mineinfo .detail {
  color: #ffffff;
  font-size: 16px;
  margin-left: 15px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.main-container {
  flex-grow: 1;
  overflow: auto;
}

.menu-container {
  display: flex;
  flex-direction: column;
  padding-top: 15px;
}

.menu-container .menu-item {
  padding: 15px;
  display: flex;
  align-items: center;
}

.menu-container .menu-item .icon-left {
  width: 25px;
  height: 25px;
  flex-shrink: 0;
}

.menu-container .menu-item .label {
  font-size: 14px;
  flex-grow: 1;
}

.menu-container .menu-item .icon-right {
  width: 7px;
  height: 14px;
  flex-shrink: 0;
}

.dividing-line {
  height: 8px;
  background-color: #f4f7f7;
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
</style>