<template>
  <div class="home-container">
    <!-- 数据概览卡片 -->
    <div class="stats-grid">
      <el-card class="stat-card">
        <div class="stat-item">
          <div class="stat-info">
            <p class="stat-label">总房间数</p>
            <p class="stat-value">120</p>
          </div>
          <el-icon class="stat-icon"><building /></el-icon>
        </div>
      </el-card>
      <el-card class="stat-card">
        <div class="stat-item">
          <div class="stat-info">
            <p class="stat-label">已入住</p>
            <p class="stat-value">86</p>
          </div>
          <el-icon class="stat-icon"><user-check /></el-icon>
        </div>
      </el-card>
      <el-card class="stat-card">
        <div class="stat-item">
          <div class="stat-info">
            <p class="stat-label">空房数</p>
            <p class="stat-value">34</p>
          </div>
          <el-icon class="stat-icon"><home /></el-icon>
        </div>
      </el-card>
      <el-card class="stat-card">
        <div class="stat-item">
          <div class="stat-info">
            <p class="stat-label">本月新增</p>
            <p class="stat-value">12</p>
          </div>
          <el-icon class="stat-icon"><plus-circle /></el-icon>
        </div>
      </el-card>
    </div>

    <!-- 主题图片卡片 -->
    <el-card class="home-card">
      <template #header>
        <div class="card-header">
          <span>公寓概览</span>
        </div>
      </template>
      <img
        src="@/assets/images/hotel.jpg"
        alt="公寓环境"
        class="home-img"
      />
      <div class="img-desc">
        智慧公寓管理平台致力于为管理员提供高效的房间管理、入住统计等功能，
        实时监控公寓状态，提升管理效率。
      </div>
    </el-card>
  </div>
</template>

<script setup lang="ts">
</script>

<style scoped>
.home-container {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* 数据统计卡片 */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}
.stat-card {
  border-radius: 8px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.05);
}
.stat-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
}
.stat-info {
  display: flex;
  flex-direction: column;
}
.stat-label {
  font-size: 14px;
  color: #606266;
  margin-bottom: 5px;
}
.stat-value {
  font-size: 24px;
  font-weight: 600;
  color: #2f5496;
}
.stat-icon {
  font-size: 36px;
  color: #409eff;
  opacity: 0.8;
}

/* 主题图片卡片 */
.home-card {
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.05);
}
.card-header {
  display: flex;
  justify-content: center;
  font-size: 18px;
  font-weight: 500;
  color: #304156;
}
.home-img {
  width: 100%;
  height: 400px;
  object-fit: cover;  /* 图片裁剪适配，避免拉伸 */
  border-radius: 4px;
}
.img-desc {
  padding: 15px;
  text-align: center;
  color: #606266;
  line-height: 1.6;
}
</style>
