<template>
  <el-footer>copyright &copy; 2021 EthanLoo</el-footer>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'GlobalFooter',
  setup () {
    return {}
  }
})
</script>

<style scoped>
.el-footer{
  position: fix;
  line-height: 60px;
  text-align: center;
  bottom: 0;
}
</style>
