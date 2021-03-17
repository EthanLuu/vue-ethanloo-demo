<template>
  <el-form :model="loginForm" class="login-form" :rules="rules" status-icon>
    <el-form-item prop="email">
      <el-input v-model="loginForm.email" placeholder="邮箱"></el-input>
    </el-form-item>
    <el-form-item prop="password">
      <el-input
        v-model="loginForm.password"
        type="password"
        placeholder="密码"
        @keyup.enter="handleLogin"
      ></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="handleLogin" class="login-btn">登陆</el-button>
    </el-form-item>
    <div class="tiparea">
      <p>
        <el-link type="primary">忘记密码？</el-link>
      </p>
    </div>
    <el-divider></el-divider>
    <el-form-item class="register-area">
      <el-button type="success" class="register-btn">新建账户</el-button>
    </el-form-item>
  </el-form>
</template>

<script lang='ts'>
import { defineComponent, ref, reactive } from 'vue'
import { useRouter } from 'vue-router'
import { useStore } from 'vuex'
import { ElMessage } from 'element-plus'
export default defineComponent({
  name: 'LoginForm',
  setup () {
    const loginForm = reactive({
      email: '',
      password: ''
    })
    const router = useRouter()
    const rules = ref({
      email: [
        {
          type: 'email',
          message: '邮箱格式错误',
          required: 'true',
          trigger: 'blur'
        }
      ],
      password: [
        {
          message: '请输入密码',
          required: 'true',
          trigger: 'blur'
        },
        {
          max: 30,
          min: 6,
          message: '密码长度不合法',
          required: 'true',
          trigger: 'blur'
        }
      ]
    })

    const store = useStore()
    const handleLogin = () => {
      if (loginForm.email === 'a@mail.com' && loginForm.password === '123456') {
        console.log('LOG IN!')
        router.push('/')
        store.commit('login')
      } else {
        ElMessage.error('请使用邮箱：a@mail.com 密码：123456 来进行登陆')
      }
    }
    return { loginForm, rules, handleLogin }
  }
})
</script>

<style scoped>
.login-form {
  width: 400px;
  text-align: center;
  padding: 10px 10px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1), 0 8px 16px rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
  margin: 40px 0 0;
}
.el-input {
  font-size: 1rem;
}
.login-btn {
  width: 100%;
  font-size: 1.2rem;
}
.register-btn {
  font-size: 1.2rem;
}
.register-area {
  margin-bottom: 10px;
}
</style>
