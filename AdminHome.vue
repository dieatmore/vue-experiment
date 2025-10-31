<template>
  <el-container class="admin-container">
    <!-- 顶部导航栏（不变） -->
    <el-header class="admin-header">
      <div class="header-left">
        <el-icon class="logo-icon"><apartment /></el-icon>
        <span class="system-name">智慧公寓管理系统</span>
      </div>
      <div class="header-right">
        <el-badge is-dot class="notification-badge">
          <el-icon class="header-icon"><bell /></el-icon>
        </el-badge>
        <div class="user-info">
          <span class="user-name">{{ userName }}</span>
          <el-dropdown trigger="click" placement="bottom-end">
            <el-icon class="dropdown-icon"><arrow-down /></el-icon>
            <template #dropdown>
              <el-dropdown-menu>
                <el-dropdown-item @click="handleLogout">退出登录</el-dropdown-item>
              </el-dropdown-menu>
            </template>
          </el-dropdown>
        </div>
      </div>
    </el-header>

    <!-- 主体布局：侧边栏 + 主内容 -->
    <el-container>
      <!-- 左侧导航栏：修改点击/悬浮背景色 -->
      <el-aside width="210px" class="admin-aside">
        <el-menu
          default-active="/admin/home"
          class="admin-menu"
          router
          unique-opened
          active-text-color="#ffffff"
        >
          <el-menu-item index="/admin/home">
            <el-icon><house-filled /></el-icon>
            <span>首页</span>
          </el-menu-item>
          <el-sub-menu index="2">
            <template #title>
              <el-icon><building /></el-icon>
              <span>公寓房间管理</span>
            </template>
            <el-menu-item index="/admin/room/list">房间列表</el-menu-item>
            <el-menu-item index="/admin/room/status">房间状态</el-menu-item>
            <el-menu-item index="/admin/room/facility">房间设施</el-menu-item>
          </el-sub-menu>
          <el-sub-menu index="3">
            <template #title>
              <el-icon><user /></el-icon>
              <span>公寓入住管理</span>
            </template>
            <el-menu-item index="/admin/checkin/user">用户入住</el-menu-item>
            <el-menu-item index="/admin/checkin/checkout">用户退房</el-menu-item>
          </el-sub-menu>
          <el-menu-item index="/admin/statistic">
            <el-icon><bar-chart /></el-icon>
            <span>入住统计</span>
          </el-menu-item>
        </el-menu>
      </el-aside>

      <!-- 主内容区（不变） -->
      <el-main class="admin-main">
        <el-breadcrumb class="breadcrumb" separator="/">
          <el-breadcrumb-item :to="{ path: '/admin/home' }">首页</el-breadcrumb-item>
        </el-breadcrumb>
        <RouterView />
      </el-main>
    </el-container>
  </el-container>
</template>

<script setup lang="ts">
// 补充缺失的图标导入（避免报错）
import {Bell, ArrowDown, User} from '@element-plus/icons-vue'
import { RouterView } from 'vue-router'
import { ref } from 'vue'
import router from '@/router'

const userName = ref(localStorage.getItem('userName') || '管理员')

const handleLogout = () => {
  localStorage.removeItem('adminToken')
  router.push('/')
}
</script>

<style scoped>
.admin-container {
  height: 100vh;
  overflow: hidden;
}

/* 顶部导航栏（不变） */
.admin-header {
  background-color: #2f5496;
  color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  height: 60px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  z-index: 10;
}
.header-left {
  display: flex;
  align-items: center;
  gap: 12px;
}
.logo-icon {
  font-size: 24px;
}
.system-name {
  font-size: 18px;
  font-weight: 500;
}
.header-right {
  display: flex;
  align-items: center;
  gap: 20px;
}
.header-icon {
  font-size: 20px;
  cursor: pointer;
}
.notification-badge {
  position: relative;
}
.user-info {
  display: flex;
  align-items: center;
  gap: 8px;
}
.user-name {
  font-size: 14px;
}
.dropdown-icon {
  font-size: 16px;
  cursor: pointer;
  opacity: 0.8;
}

/* 左侧侧边栏：核心修改部分 */
.admin-aside {
  background-color: #304156; /* 侧边栏底色不变 */
  color: #bfcbd9;
  height: calc(100vh - 60px);
}
.admin-menu {
  border-right: none;
  height: 100%;
  padding-top: 15px;
}
/* 菜单item基础样式 */
.admin-menu :deep(.el-menu-item),
.admin-menu :deep(.el-sub-menu__title) {
  height: 50px;
  line-height: 50px;
  padding-left: 30px !important;
  font-size: 14px;
  transition: all 0.2s ease; /* 平滑过渡效果 */
}
/* 点击选中状态：改用深蓝色，而非黑色 */
.admin-menu :deep(.el-menu-item.is-active) {
  background-color: #2563eb; /* 亮蓝色背景 */
  color: #ffffff; /* 白色文字 */
}
/* 悬浮状态：改用浅灰色，而非深黑 */
.admin-menu :deep(.el-menu-item:hover),
.admin-menu :deep(.el-sub-menu__title:hover) {
  background-color: #475569; /* 浅灰色背景 */
  color: #ffffff; /* 悬浮时文字变白 */
}

/* 主内容区（不变） */
.admin-main {
  padding: 20px;
  background-color: #f5f7fa;
  height: calc(100vh - 60px);
  overflow-y: auto;
}
.breadcrumb {
  margin-bottom: 20px;
  font-size: 14px;
}
</style>
