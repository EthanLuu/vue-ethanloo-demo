<template>
  <el-container class="home">
    <div class="headerWrapper">
      <el-header>
        <global-header :user="currentUser"></global-header>
      </el-header>
    </div>
    <el-container class="content">
      <nav-menu />
      <el-container>
        <el-main>
          <router-view></router-view>
          <global-footer />
        </el-main>
      </el-container>
    </el-container>
  </el-container>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue'
import { useStore } from 'vuex'
import GlobalHeader from './components/GlobalHeader.vue'
import NavMenu from './components/NavMenu.vue'
import GlobalFooter from './components/GlobalFooter.vue'

export default defineComponent({
  name: 'App',
  components: {
    GlobalHeader,
    NavMenu,
    GlobalFooter
  },
  methods: {},
  setup () {
    const store = useStore()
    const currentUser = computed(() => store.state.user)
    return {
      currentUser
    }
  }
})
</script>

<style>
.el-main {
  background-color: #fff;
}
.el-container {
  position: relative;
  width: 100%;
  height: 100%;
}
.el-header {
  height: 80px;
  box-sizing: border-box;
  border-bottom: 1px solid #dcdfe6;
  display: block;
  background-color: #fff;
}
.headerWrapper {
  position: fixed;
  top: 0px;
  width: 100%;
  z-index: 2000;
}
.content {
  margin-top: 60px;
}
body.is-component,
html.is-component {
  overflow: hidden;
}
body,
html {
  margin: 0;
  padding: 0;
  height: 100%;
  font-family: Helvetica Neue, Helvetica, PingFang SC, Hiragino Sans GB,
    Microsoft YaHei, SimSun, sans-serif;
  font-weight: 400;
  -webkit-font-smoothing: antialiased;
  -webkit-tap-highlight-color: transparent;
}
</style>
