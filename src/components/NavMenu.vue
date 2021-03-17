<template>
  <el-aside width="200px">
    <el-menu
      default-active="0"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
    >
      <el-menu-item index="0">
        <i class="el-icon-menu"></i>
        <template #title>导航二</template>
      </el-menu-item>
      <el-submenu index="1" disabled>
        <template #title>
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
      </el-submenu>
      <el-menu-item index="2" disabled>
        <i class="el-icon-document"></i>
        <template #title>导航三</template>
      </el-menu-item>
    </el-menu>
  </el-aside>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'NavMenu',
  setup () {
    return {}
  }
})
</script>

<style scoped>
.el-menu {
  top: 60px;
  bottom: 0;
  width: 200px;
  transition: width 0.28s;
  width: 210px !important;
  height: 100%;
  position: fixed;
  left: 0;
  z-index: 1001;
  overflow: hidden;
}
</style>
