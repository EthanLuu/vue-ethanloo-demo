<template>
  <el-row type="flex" class="row-bg">
    <el-col :span="6">
      <router-link to="/" type="primary" class="el-link">
        <div class="logo">SooMooc</div>
      </router-link>
    </el-col>
    <el-col :span="6">
      <div v-if="!user.isLogin" class="btn-group">
        <router-link to="/login">
          <el-button class="register-btn">注册</el-button>
        </router-link>
        <router-link to="/login">
          <el-button class="login-btn">登陆</el-button>
        </router-link>
      </div>
      <div v-else class="user-group">
        <drop-down :title="`${user.name}`"></drop-down>
      </div>
    </el-col>
  </el-row>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import DropDown from './DropDown.vue'

export interface UserProps {
  isLogin: boolean;
  name?: string;
  id?: number;
}
export default defineComponent({
  name: 'GlobalHeader',
  components: {
    DropDown
  },
  methods: {},
  props: {
    user: {
      type: Object as PropType<UserProps>,
      required: true
    }
  }
})
</script>

<style scoped>
.logo {
  color: #409eff;
  font-size: 2rem;
}
.row-bg {
  justify-content: space-between;
  align-items: center;
  height: 100%;
}
.btn-group {
  float: right;
  overflow: hidden;
}
.user-group {
  float: right;
}
.login-btn {
  margin-left: 20px;
}
</style>
