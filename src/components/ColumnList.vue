<template>
  <el-row :gutter="20">
    <el-col :span="6" v-for="column in columnList" :key="column.id">
      <el-card class="box-card" :body-style="{ padding: '0px' }" shadow="always">
        <div class="demo">
          <el-image
            fit="cover"
            class="cover"
            :src="column.avatar"
            :alt="column.title"
            @click="toRoom(column.id)"
          ></el-image>
        </div>

        <div style="padding: 14px;">
          <div class="room-title">
            <span @click="toRoom(column.id)">{{column.title}}</span>
          </div>
        </div>
      </el-card>
    </el-col>
  </el-row>
</template>

<script lang='ts'>
import { defineComponent, PropType, computed } from 'vue'
import { ColumnProps } from '../testData'
import { useRouter } from 'vue-router'

export default defineComponent({
  name: 'ConlumnList',
  props: {
    list: {
      type: Array as PropType<ColumnProps[]>,
      required: true
    }
  },
  setup (props) {
    const columnList = computed(() => {
      return props.list.map(column => {
        if (!column.avatar) {
          column.avatar = require('@/assets/404.png')
        }
        return column
      })
    })
    const router = useRouter()
    const toRoom = (roomId: number) => {
      router.push({ name: 'column', params: { id: roomId } })
    }
    return {
      columnList,
      toRoom
    }
  }
})
</script>

<style scoped scss>
.el-col {
  border-radius: 4px;
  margin-bottom: 20px;
}
.demo {
  height: 150px;
  width: 100%;
}
.cover {
  cursor: pointer;
  height: 150px;
}
.bottom {
  margin-top: 13px;
  line-height: 12px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.room-title {
  text-align: center;
}
.room-title > span {
  cursor: pointer;
}
</style>
