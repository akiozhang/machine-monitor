<template>
  <div class="mod-home">
    <div class="mod-container">
      <div class="mod-home__select">
        <el-select v-model="value" placeholder="请选择">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
      </div>
      <div class="mod-home__video">
        <video src="static/video/test.mp4" controls="controls"></video>
      </div>
    </div>
    <div class="mod-container__title">
      <span>报警信息</span>
    </div>
    <div class="mod-home__table">
      <b-table></b-table>
    </div>
  </div>
</template>

<script>
  import bTable from '@/components/table'
  export default {
    name: 'home',
    components: {
      bTable
    },
    data () {
      return {
        options: [{
          value: '001',
          label: '设备1'
        }, {
          value: '002',
          label: '设备2'
        }, {
          value: '003',
          label: '设备3'
        }, {
          value: '004',
          label: '设备4'
        }, {
          value: '005',
          label: '设备5'
        }],
        value: '001',
        centerDialogVisible: false
      }
    },
    computed: {
      getMachineTitle () {
        let _this = this
        let result = ''
        _this.options.forEach((item) => { if (item['value'] === _this.value) result = item['label'] })
        return result
      }
    },
    methods: {
      onClickMachine () {
        console.log(this.getMachineTitle)
        this.centerDialogVisible = true
      }
    }
  }
</script>

<style lang="scss" scoped>
  .mod-home {
    line-height: 1.5;
    &__select{
      width: 20%;
      min-width: 200px;
    }
    &__video{
      text-align: center;
      video{
        max-height: 300px;
        width: 80%;
      }
    }
  }
  .mod-container{
    min-height: 100px;
    line-height: 100px;
    &__title{
      font-size: 20px;
      padding: 20px;
      font-weight: bold;
   }
  }
</style>

