<script setup lang="ts"></script>

<template>
  <view class="content">
    <uni-forms ref="formRef">
      <!-- 表单内容 -->
      <uni-forms-item name="receiver" class="form-item">
        <text class="label">收货人</text>
        <input class="input" placeholder="请填写收货人姓名" />
      </uni-forms-item>
      <uni-forms-item name="contact" class="form-item">
        <text class="label">手机号码</text>
        <input class="input" placeholder="请填写收货人手机号码" :maxlength="11" />
      </uni-forms-item>
      <uni-forms-item name="countyCode" class="form-item">
        <text class="label">所在地区</text>
        <!-- #ifdef MP-WEIXIN -->
        <picker class="picker" mode="region">
          <view v-if="false">{{}}</view>
          <view v-else class="placeholder">请选择省/市/区(县)</view>
        </picker>
        <!-- #endif -->

        <!-- #ifdef H5 || APP-PLUS -->
        <uni-data-picker
          placeholder="请选择地址"
          popup-title="请选择城市"
          collection="opendb-city-china"
          field="code as value, name as text"
          orderby="value asc"
          :step-searh="true"
          self-field="code"
          parent-field="parent_code"
          :clear-icon="false"
        />
        <!-- #endif -->
      </uni-forms-item>
      <uni-forms-item name="address" class="form-item">
        <text class="label">详细地址</text>
        <input class="input" placeholder="街道、楼牌号等信息" />
      </uni-forms-item>
      <view class="form-item">
        <label class="label">设为默认地址</label>
        <switch class="switch" color="#27ba9b" :checked="true" />
      </view>
    </uni-forms>
  </view>
  <!-- 提交按钮 -->
  <button class="button">保存并使用</button>
</template>

<style lang="scss">
// 深度选择器修改 uni-data-picker 组件样式
:deep(.selected-area) {
  flex: 0 1 auto;
  height: auto;
}

page {
  background-color: #f4f4f4;
}

.content {
  margin: 20rpx 20rpx 0;
  padding: 0 20rpx;
  border-radius: 10rpx;
  background-color: #fff;

  .form-item,
  .uni-forms-item {
    display: flex;
    align-items: center;
    min-height: 96rpx;
    padding: 25rpx 10rpx;
    background-color: #fff;
    font-size: 28rpx;
    border-bottom: 1rpx solid #ddd;
    position: relative;
    margin-bottom: 0;

    // 调整 uni-forms 样式
    .uni-forms-item__content {
      display: flex;
    }

    .uni-forms-item__error {
      margin-left: 200rpx;
    }

    &:last-child {
      border: none;
    }

    .label {
      width: 200rpx;
      color: #333;
    }

    .input {
      flex: 1;
      display: block;
      height: 46rpx;
    }

    .switch {
      position: absolute;
      right: -20rpx;
      transform: scale(0.8);
    }

    .picker {
      flex: 1;
    }

    .placeholder {
      color: #808080;
    }
  }
}

.button {
  height: 80rpx;
  margin: 30rpx 20rpx;
  color: #fff;
  border-radius: 80rpx;
  font-size: 30rpx;
  background-color: #27ba9b;
}
</style>
