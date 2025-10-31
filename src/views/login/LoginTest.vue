<template>
  <div>
    <div class="container-all">
      <HelpFilled class="icon-test" />
      <span class="title-top">智慧公寓</span>
    </div>
  </div>
  <div class="container-img">
    <img src="../../assets/images/View.jpg" alt="校园风景" class="backimg" />
  </div>
  <div class="right-section">
    <el-card class="box-card">
      <div>
        <p class="card-text">账号密码登录</p>
      </div>

      <LoginForm />
    </el-card>
  </div>
</template>
<script setup lang="ts">
import { HelpFilled } from '@element-plus/icons-vue'
import LoginForm from './LoginForm1.vue'
</script>
<style scoped>
.container-all {
  display: flex;
  align-items: center;
  margin-left: 1.5rem;
  margin-top: 0.75rem;
}
.icon-test {
  width: 4rem;
  height: 4rem;
}
.backimg {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.title-top {
  font-size: 1.875rem /* 30px */;
  line-height: 2.25rem /* 36px */;
  margin-left: 1rem /* 16px */;
}
.container-img {
  position: fixed;
  top: 10%;
  left: 0;
  width: 100%;
  height: 90%;
  z-index: -1;
  overflow: hidden;
}
.header-img {
  width: 100px;
  height: 100px;
}
.right-section {
  position: fixed;
  right: 18%;
  top: 55%;
  transform: translateY(-50%);
}
.box-card {
  padding: 12px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.95);
  border-radius: 16px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.05);
}
.card-text {
  font-weight: bolder;
  font-size: 1.5rem;
  font-family: 'Microsoft YaHei', sans-serif;
  margin-bottom: 25px;
  color: #333;
  text-align: center;
}
.el-card.is-always-shadow {
  border-radius: 14px;
}
</style>
