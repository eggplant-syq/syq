<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
import { ref } from "vue";

const username = ref("");
const password = ref("");
const usernameError = ref("");
const passwordError = ref("");

const onSubmit = () => {
  usernameError.value = "";
  passwordError.value = "";

  // 检查账号
  if (!username.value) {
    usernameError.value = "请输入账号";
    return;
  }
  if (!username.value.match(/^[a-zA-Z0-9]{5,8}$/)) {
    usernameError.value = "账号为5-8位数字和字母";
    return;
  }

  // 检查密码
  if (!password.value) {
    passwordError.value = "请输入密码";
    return;
  }
  if (!password.value.match(/^[a-zA-Z0-9]{5,12}$/)) {
    passwordError.value = "密码为5-12位数字和字母";
    return;
  }

  // 执行登录操作
  console.log("登录", username.value, password.value);
  // 这里可以发送请求到后端进行验证
};
</script>
<template>
  <div class="father">
    <div class="left">
      <img src="../../public/images/1.png" alt="" />
    </div>

    <!-- <div class="right">
      <h1 class="text">登录，即刻创造您的应用</h1>
      <div>
        <input
          type="text"
          placeholder="账号"
          v-model="username"
          id="username"
        /></br>
        <input
          type="password"
          placeholder="密码"
          v-model="password"
          id="password"
        />
      </div>
      <button>提交</button>
    </div> -->
    <form @submit.prevent="onSubmit">
      <div>
        <label for="username">账号:</label>
        <input
          type="text"
          id="username"
          v-model="username"
          placeholder="请输入账号"
          required
          pattern="[a-zA-Z0-9]{5,8}"
          title="账号为5-8位数字和字母"
        />
        <span v-if="usernameError" class="error">{{ usernameError }}</span>
      </div>
      <div>
        <label for="password">密码:</label>
        <input
          type="password"
          id="password"
          v-model="password"
          placeholder="请输入密码"
          required
          pattern="[a-zA-Z0-9]{5,12}"
          title="密码为5-12位数字和字母"
        />
        <span v-if="passwordError" class="error">{{ passwordError }}</span>
      </div>
      <button type="submit">登录</button>
    </form>
  </div>
</template>

<style>
* {
  padding: 0;
  margin: 0;
}
.father {
  display: flex;
}
.left {
  /* width: 1152px; */
  width: 30%;
  height: 700px;
  overflow: hidden;
}
.left-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.right {
  /* width: 1748px; */
  width: 60%;
}
.text {
  padding-top: 200px;
  margin-left: 180px;
}
</style>
