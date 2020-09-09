<template>
  <el-table
    :data="dataList"
    border
    v-loading="dataListLoading"
    @selection-change="selectionChangeHandle"
    style="width: 100%;">
<!--    <el-table-column-->
<!--      type="selection"-->
<!--      header-align="center"-->
<!--      align="center"-->
<!--      width="50">-->
<!--    </el-table-column>-->
    <el-table-column
      prop="number"
      header-align="center"
      align="center"
      width="80"
      label="相机编号">
    </el-table-column>
    <el-table-column
      prop="remark"
      header-align="center"
      align="center"
      label="相机IP">
    </el-table-column>
    <el-table-column
      prop="jobId"
      header-align="center"
      align="center"
      width="80"
      label="事件类型">
    </el-table-column>
    <el-table-column
      prop="beanName"
      header-align="center"
      align="center"
      label="事件描述">
    </el-table-column>
    <el-table-column
      prop="params"
      header-align="center"
      align="center"
      label="危险等级">
    </el-table-column>
    <el-table-column
      prop="status"
      header-align="center"
      align="center"
      label="状态">
      <template slot-scope="scope">
        <el-tag v-if="scope.row.status === 0" size="small">正常</el-tag>
        <el-tag v-else size="small" type="danger">暂停</el-tag>
      </template>
    </el-table-column>
<!--    <el-table-column-->
<!--      fixed="right"-->
<!--      header-align="center"-->
<!--      align="center"-->
<!--      width="150"-->
<!--      label="操作">-->
<!--      <template slot-scope="scope">-->
<!--        <el-button v-if="isAuth('sys:schedule:update')" type="text" size="small" @click="addOrUpdateHandle(scope.row.jobId)">修改</el-button>-->
<!--        <el-button v-if="isAuth('sys:schedule:delete')" type="text" size="small" @click="deleteHandle(scope.row.jobId)">删除</el-button>-->
<!--        <el-button v-if="isAuth('sys:schedule:pause')" type="text" size="small" @click="pauseHandle(scope.row.jobId)">暂停</el-button>-->
<!--        <el-button v-if="isAuth('sys:schedule:resume')" type="text" size="small" @click="resumeHandle(scope.row.jobId)">恢复</el-button>-->
<!--        <el-button v-if="isAuth('sys:schedule:run')" type="text" size="small" @click="runHandle(scope.row.jobId)">立即执行</el-button>-->
<!--      </template>-->
<!--    </el-table-column>-->
  </el-table>
</template>

<script>
  export default {
    name: 'index',
    data () {
      return {
        dataForm: {
          beanName: ''
        },
        dataList: [],
        pageIndex: 1,
        pageSize: 10,
        totalPage: 0,
        dataListLoading: false,
        dataListSelections: [],
        addOrUpdateVisible: false,
        logVisible: false
      }
    },
    methods: {
      selectionChangeHandle (val) {
        this.dataListSelections = val
      }
    }
  }
</script>

<style scoped>

</style>
