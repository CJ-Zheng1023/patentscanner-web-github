<template>
  <div class="app-container">
    <div class="wrapper clearfix">
      <div class="left">
        <div class="panel">
          <div class="panel-header">
            <div class="start">
              <div class="title">待审文献列表</div>
            </div>
          </div>
          <div class="panel-body no-padding">
            <table cellspacing="0" cellpadding="0" border="0" class="table">
              <thead>
              <tr>
                <th style="width: 60px">
                  <div class="cell">序号</div>
                </th>
                <th>
                  <div class="cell">发明名称</div>
                </th>
              </tr>
              </thead>
              <tbody>
              <tr v-for="(item, index) in cases">
                <td class="center">
                  <div class="cell">
                    <span class="circle">{{index + 1}}</span>
                  </div>
                </td>
                <td>
                  <div class="cell">{{item.name}}</div>
                </td>
              </tr>
              </tbody>
            </table>
          </div>
          <div class="panel-footer center">
            <el-pagination :current-page="1" :page-size="10" layout="prev, jumper, next, total" :total="60"></el-pagination>
          </div>
        </div>
      </div>
      <div class="right">
        <div class="panel panel-info">
          <div class="panel-header">
            <div class="start">
              <div class="title">对比文献列表</div>
            </div>
            <div class="end">
              <div class="btn-group" style="line-height: 1">
                <button type="button" class="btn btn-info btn-icon"><i class="iconfont miit-icon-view"></i>全部预览</button>
                <button type="button" class="btn btn-info btn-icon"><i class="iconfont miit-icon-preview"></i>预览报告</button>
              </div>
            </div>
          </div>
          <div class="panel-body no-padding">
            <table cellspacing="0" cellpadding="0" border="0" class="table">
              <thead>
              <tr>
                <th style="width: 15%">
                  <div class="cell">申请号</div>
                </th>
                <th  style="width: 30%">
                  <div class="cell">发明名称</div>
                </th>
                <th  style="width: 19%">
                  <div class="cell">公开日</div>
                </th>
                <th  style="width: 18%">
                  <div class="cell">相似度</div>
                </th>
                <th  style="width: 18%">
                  <div class="cell">操作</div>
                </th>
              </tr>
              </thead>
              <tbody>
              <tr v-for="item in patents">
                <td class="center">
                  <div class="cell">{{item.ap}}</div>
                </td>
                <td>
                  <div class="cell">{{item.name}}</div>
                </td>
                <td class="center">
                  <div class="cell">{{item.pd}}</div>
                </td>
                <td class="center">
                  <div class="cell">
                    <span :class="[item.score > 50 ? 'high' : 'low']">{{item.score + '%'}}</span>
                  </div>
                </td>
                <td class="center">
                  <div class="cell">
                    <button type="button" class="btn btn-primary is-plain btn-radis btn-xs btn-icon">
                      <i class="el-icon-view"></i>
                      浏 览
                    </button>
                  </div>
                </td>
              </tr>
              </tbody>
            </table>
          </div>
          <div class="panel-footer center">
            <el-pagination style="height: 32px;" :current-page="1" :page-size="10" layout="prev, jumper, next, total" :total="60"></el-pagination>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      cases: [{
        name: '景区自助旅游系统'
      },{
        name: '基于移动互联网的景区自助旅游系统'
      },{
        name: '基于移动互联网的景区自助旅游系统'
      },{
        name: '基于移动互联网'
      },{
        name: '基于移动互联网的景区自助旅游系统'
      },{
        name: '基于景区自助旅游系统'
      },{
        name: '基于移动互联网的景区自助旅游系统'
      },{
        name: '基于移动互联网的景区自助旅游系统网的景区自助'
      },{
        name: '基于移动互联网的景区网的景区自助系统'
      },{
        name: '自助旅游系统'
      }],
      patents: [{
        ap: 'CN123123',
        name: '紧急呼叫处理',
        pd: '2012.08.12',
        score: 80
      },{
        ap: 'CN123123',
        name: '紧急呼叫处理',
        pd: '2012.08.12',
        score: 80
      },{
        ap: 'CN123123',
        name: '紧急呼叫处理',
        pd: '2012.08.12',
        score: 80
      },{
        ap: 'CN123123',
        name: '紧急呼叫处理紧急呼叫处理紧急呼叫处理',
        pd: '2012.08.12',
        score: 80
      },{
        ap: 'CN123123',
        name: '紧急呼叫处理',
        pd: '2012.08.12',
        score: 80
      },{
        ap: 'CN123123',
        name: '紧急呼叫处理',
        pd: '2012.08.12',
        score: 80
      },{
        ap: 'CN123123',
        name: '紧急呼叫处理紧急呼叫处理紧急呼叫处理紧急呼叫处理紧急呼叫处理',
        pd: '2012.08.12',
        score: 50
      },{
        ap: 'CN123123',
        name: '紧急呼叫处理',
        pd: '2012.08.12',
        score: 49
      },{
        ap: 'CN123123',
        name: '紧急呼叫处理',
        pd: '2012.08.12',
        score: 30
      },{
        ap: 'CN123123',
        name: '紧急呼叫处理',
        pd: '2012.08.12',
        score: 20
      }]
    }
  }
}
</script>
<style scoped lang="scss">
  $leftSideWidth: 320px;
  .left{
    float: left;
    width: $leftSideWidth;
  }
  .right{
    margin-left: $leftSideWidth + 10px;
  }
  .score{
    font-size: 15px;
    &.high{
      color: rgb(233, 84, 65);
    }
    &.low{
      color: rgb(79, 137, 250);
    }
  }
  .table th .cell, .table td .cell{
    padding: 0 15px;
  }
  .cell{
    & .sub, .title{
      width: 100%;
      text-overflow: ellipsis;
      overflow: hidden;
      white-space: nowrap;
    }
  }
  .cell .sub{
    font-size: 14px;
    color: rgb(152, 153, 152);
    margin-bottom: 4px;
  }
  .cell .title{
    font-size: 15px;
    color: rgb(105, 105, 104);
  }
  .table{
    border: none;
  }
  .btn-icon i.iconfont{
    font-size: 20px;
    vertical-align: middle;
  }
</style>
