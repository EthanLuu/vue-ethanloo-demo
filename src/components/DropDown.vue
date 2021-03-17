<template>
  <el-dropdown>
    <span class="el-dropdown-link">
      {{title}}
      <i class="el-icon-arrow-down el-icon--right"></i>
    </span>
    <template #dropdown>
      <el-dropdown-menu>
        <el-dropdown-item>黄金糕</el-dropdown-item>
        <el-dropdown-item>狮子头</el-dropdown-item>
        <el-dropdown-item>螺蛳粉</el-dropdown-item>
      </el-dropdown-menu>
    </template>
  </el-dropdown>
</template>

<script lang='ts'>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'DropDown',
  props: {
    title: {
      type: String,
      required: true
    }
  }
})
</script>

<style scoped scss>
.el-dropdown-link {
  cursor: pointer;
}
.el-icon-arrow-down {
  font-size: 12px;
}
</style>
