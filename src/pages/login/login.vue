<template>
  <view class="login">
    <view class="logo" style="color: aqua">智慧农业环境监测系统</view>
    <view class="logo" style="font-size: large">智慧农业后台管理系统</view>
    <view class="form">
      <view class="input">
        <input type="text" placeholder="请输入用户名" />
      </view>
      <view class="input">
        <input type="password" password placeholder="请输入密码" />
      </view>
      <button class="submit" @click="login">登录</button>
    </view>
    <text class="help">忘记密码?</text>
    <text class="registrate" style="float: right">注册账号</text>
  </view>
</template>

<style>
.login {
  position: absolute;
  top: 30%;
  left: 50%;
  width: 80%;
  transform: translate(-50%, -50%);
}
.logo {
  text-align: center;
  margin-bottom: 40rpx;
  font-size: medium;
}
.form {
  margin-bottom: 40rpx;
}
.input {
  display: flex;
  align-items: center;
  border: 1rpx solid #ddd;
  padding: 20rpx 0;
  border-radius: 30rpx;
  margin: 20rpx;
}
.icon {
  padding: 0 10rpx;
}
.submit {
  background: skyblue;
  color: #fff;
  margin-top: 40rpx;
}
.help .registrate {
  text-align: center;
}
</style>

<script>
export default {
  methods: {
    login() {
      // 登录逻辑
      uniCloud.callFunction({
        name: 'login',
        data: {}
        success: (result) => {},
        fail: (error) => {}
      })
      let success = true;
      if (success) {
        uni.switchTab({
          url: "/pages/home/home",
        });
      }
    },
  },
};
</script>
