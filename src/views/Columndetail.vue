<template>
  <div class="detail">
    <el-container>
      <el-main>
        <div class="block">
          <el-image
            class="cover"
            :src="column.avatar"
            fit="contain"
            :preview-src-list="[column.avatar]"
          ></el-image>
        </div>
      </el-main>
      <el-aside width="300px" class='right-side'>
        <div class="tags">
          <el-tag v-for="tag in column.tags" :key="tag">{{tag}}</el-tag>
        </div>
        <div class="desc">{{column.description}}</div>
      </el-aside>
    </el-container>
  </div>
</template>
<script lang='ts'>
import { defineComponent, computed } from 'vue'
import { useRoute } from 'vue-router'
import { useStore } from 'vuex'

export default defineComponent({
  setup () {
    const route = useRoute()
    const store = useStore()
    const currentId = +route.params.id
    const column = computed(() => store.getters.getColumnById(currentId))
    return {
      column
    }
  }
})
</script>

<style scoped>
.tags {
  margin-bottom: 10px;
}
.el-tag {
  margin-right: 10px;
}
.detail {
  box-sizing: border-box;
}
.cover {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.12), 0 0 6px rgba(0, 0, 0, 0.04);
  margin: 0 auto;
  border-radius: 6px;
}
.el-main{
  padding: 0px;
}
.right-side {
  padding: 0px 20px;
}
</style>
