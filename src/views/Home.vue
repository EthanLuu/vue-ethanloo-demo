<template>
  <el-main>
    <column-list :list="list"></column-list>
  </el-main>
</template>

<script lang='ts'>
import ColumnList from '../components/ColumnList.vue'
import { defineComponent, computed } from 'vue'
import { GlobalDataProps } from '../store'
import { useStore } from 'vuex'

export default defineComponent({
  name: 'home',
  components: {
    ColumnList
  },
  setup () {
    const store = useStore<GlobalDataProps>()
    const list = computed(() => store.state.columns)
    return {
      list
    }
  }
})

</script>

<style lang="scss" scoped>
</style>
