<template>
  <el-main>
    <login-form></login-form>
  </el-main>
</template>

<script lang='ts'>
import LoginForm from '../components/LoginForm.vue'

export default ({
  name: 'login',
  components: {
    LoginForm
  }
})

</script>

<style scoped>
  .login-form{
    margin: 50px auto;
  }
</style>
