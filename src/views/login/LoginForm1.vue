<template>
  <el-form
    :rules="rules"
    ref="formRef"
    :model="form"
    label-width="50px"
    label-position="top"
    style="width: 20rem"
  >
    <el-form-item label="账号" prop="account">
      <el-input v-model="form.account" placeholder="请输入账号" :prefix-icon="User" />
    </el-form-item>
    <el-form-item label="密码" prop="password">
      <el-input
        v-model="form.password"
        type="password"
        placeholder="请输入密码"
        :prefix-icon="Lock"
        show-password
      />
    </el-form-item>
    <el-checkbox v-model="agree" size="large" class="ml-3">
      阅读并同意
      <span class="blue-underlined">服务协议</span>
      和
      <span class="blue-underlined">个人信息保护政策</span>
    </el-checkbox>
    <el-button type="primary" class="login-button">
      <img src="../../assets/icon/Login.png" alt="登录" style="margin-left: 0.75rem" />
      登录
    </el-button>
    <el-row>
      <el-col :span="6" :offset="1" style="align-content: center">
        <a href="#" class="link-text">忘记密码？</a>
      </el-col>
      <el-col :span="6" :offset="11" style="align-content: center">
        <a href="#" class="link-text" @click.prevent="switchToRegister">免费注册</a>
      </el-col>
    </el-row>
  </el-form>
</template>

<script setup lang="ts">
import { Lock, User } from '@element-plus/icons-vue'
import type { FormInstance } from 'element-plus'
import { ref } from 'vue'

const agree = ref(false)

const emit = defineEmits<{
  switch: []
}>()

const formRef = ref<FormInstance>()

const form = ref({
  account: '',
  password: '',
})

// 表单验证规则
const rules = ref({
  account: [
    { required: true, message: '请输入账号', trigger: 'blur' },
    { min: 5, max: 20, message: '长度在5到20个字符', trigger: 'blur' },
  ],
  password: [
    { required: true, message: '请输入密码', trigger: 'blur' },
    { min: 5, max: 20, message: '长度在5到20个字符', trigger: 'blur' },
  ],
})

// 切换到注册表单
const switchToRegister = (): void => {
  emit('switch')
}
</script>

<style scoped>
.login-button {
  width: 320px;
  display: block;
  margin: 10px auto;
}

.blue-underlined {
  --tw-text-opacity: 1;
  color: rgb(59 130 246 / var(--tw-text-opacity, 1)) /* #3b82f6 */;
  text-decoration-line: underline;
}

.link-text {
  font-size: 14px;
  color: #409eff;
  transition: color 0.2s ease;
  font-weight: 500;
  text-decoration: none;
}

.link-text:hover {
  color: rgba(64, 158, 255, 0.9);
  text-decoration: underline;
}

:deep(.el-form-item__label::before) {
  content: none !important;
}

:deep(.el-form-item__label) {
  font-size: 14px;
  color: #606266;
  margin-bottom: 6px;
  font-weight: bold;
}

:deep(.el-input) {
  width: 100%;
}
</style>
