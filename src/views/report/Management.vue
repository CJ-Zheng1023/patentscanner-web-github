<template>
  <div class="app-container">
    <div class="panel">
      <div class="panel-header clearfix">
        <div class="start">
          <h4 class="title">检测报告管理</h4>
        </div>
        <div class="end">
          <div class="btn-group">
            <button type="button" class="btn btn-info btn-icon">
              <i class="el-icon-download"></i>
              下载
            </button>
            <button type="button" class="btn btn-info btn-icon"> <i class="el-icon-delete"></i>
              删除
            </button>
          </div>
        </div>
      </div>
      <div class="panel-body no-padding">
        <table cellspacing="0" cellpadding="0" border="0" class="table table-info">
          <thead>
          <tr>
            <th style="width: 50px">
              <div class="cell">
                <el-checkbox :indeterminate="isIndeterminate" v-model="allChecked" @change="checkAll"></el-checkbox>
              </div>
            </th>
            <th style="width: 80px">
              <div class="cell">序号</div>
            </th>
            <th style="width: 350px">
              <div class="cell">专利名称</div>
            </th>
            <th style="width: 250px">
              <div class="cell">生成时间</div>
            </th>
            <th>
              <div class="cell">操作</div>
            </th>
          </tr>
          </thead>
          <tbody>
          <tr v-for="(item,index) in reportTables" :key="index">
            <td class="center">
              <div class="cell">
                <el-checkbox @change="check" v-model="item.checked"></el-checkbox>
              </div>
            </td>
            <td class="center">
              <div class="cell"> <span class="circle">{{index +1}}</span></div>
            </td>
            <td>
              <div class="cell">{{item.patentName}}</div>
            </td>
            <td>
              <div class="cell">{{item.createTime}}</div>
            </td>
            <td class="center">
              <div class="cell">
                <button type="button" class="btn btn-primary is-plain btn-radis btn-xs">
                  <i class="el-icon-view"></i>
                  查 看
                </button>
                <button type="button" class="btn btn-danger is-plain btn-radis btn-xs btn-icon">
                  <i class="el-icon-delete"></i>
                  删 除
                </button>
              </div>
            </td>
          </tr>
          </tbody>
        </table>
      </div>
      <div class="panel-footer right">
        <el-pagination :current-page.sync="currentPage" :page-size="100" layout="prev, pager, next, jumper" :total="1000"></el-pagination>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      reportTables: [
        { patentName: '手机外屏历史管理装置及方法', createTime: '2019-10-10', checked: false },
        { patentName: '数据回收方法及移动终端', createTime: '2019-10-10', checked: false },
        { patentName: '一种移动终端的数据处理方法及系统', createTime: '2019-10-10', checked: false },
        { patentName: '一种浏览历史查询方法', createTime: '2019-10-10', checked: false },
        { patentName: '应用管理方法、设备、终端', createTime: '2019-10-10', checked: false }
      ],
      currentPage: 5,
      allChecked: false,
      isIndeterminate: false
    }
  },
  computed: {
    // 选中数据集合
    checked() {
      return this.reportTables.filter(item => !!item.checked)
    },
    dataSize() {
      return this.reportTables.length
    },
    checkedSize() {
      return this.checked.length
    }
  },
  methods: {
    // 全选、反选
    checkAll(val) {
      this.reportTables.forEach(item => { item.checked = !!val })
      this.allChecked = this.dataSize === this.checkedSize
      this.isIndeterminate = false
    },
    check(val) {
      this.allChecked = this.dataSize === this.checkedSize
      this.isIndeterminate = this.checkedSize > 0 && this.checkedSize < this.dataSize
    }
  }
}

</script>
