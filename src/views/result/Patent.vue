<template>
  <div class="app-container view">
    <div class="wrapper clearfix">
      <div class="left">
        <div class="panel">
          <div class="panel-header">
            <div class="start">
              <div class="title">文献列表</div>
            </div>
          </div>
          <div class="panel-body no-padding">
            <table cellspacing="0" cellpadding="0" border="0" class="table">
              <thead>
              <tr>
                <th style="width: 60px">
                  <div class="cell">序号</div>
                </th>
                <th style="width: 180px">
                  <div class="cell">申请号/发明名称</div>
                </th>
                <th>
                  <div class="cell">相似度</div>
                </th>
              </tr>
              </thead>
              <tbody>
              <tr v-for="(item, index) in patents">
                <td class="center">
                  <div class="cell">
                    <span class="circle">{{index + 1}}</span>
                  </div>
                </td>
                <td>
                  <div class="cell">
                    <div class="sub">{{item.ap}}</div>
                    <div class="title">{{item.name}}</div>
                  </div>
                </td>
                <td class="center">
                  <div class="cell">
                    <span :class="[item.score > 50 ? 'high' : 'low']">{{item.score + '%'}}</span>
                  </div>
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
              <div class="menubar">
                <ul class="menus clearfix">
                  <li class="menu-item">
                    <a hre="javascript:;">添加至对比库</a>
                  </li>
                  <li class="menu-item">
                    <a hre="javascript:;">高亮</a>
                  </li>
                  <li class="menu-item">
                    <a hre="javascript:;">高密</a>
                  </li>
                  <li class="menu-item">
                    <a hre="javascript:;">聚焦</a>
                  </li>
                  <li class="menu-item">
                    <a hre="javascript:;" @click="dialogTableVisible = true">对比库</a>
                  </li>
                </ul>
              </div>
            </div>
            <div class="end">
              <button type="button" class="btn btn-info">预览报告</button>
            </div>
          </div>
          <div class="panel-body no-padding">
            <el-tabs v-model="activeName">
              <el-tab-pane label="摘要" name="abs">
                <div class="patent-wrapper clearfix">
                  <div class="patent-content">
                    <h5 class="title origin">原文献标题:手机历史app的管理方法及系统</h5>
                    <div class="box border">
                      <div class="box-header">
                        著录项目
                      </div>
                      <div class="box-body">
                        <div class="inner">
                          <div class="information">
                            <div class="information-item">
                              <label class="label">申请号：</label>
                              <div class="content">CN123444</div>
                            </div>
                            <div class="information-item">
                              <label class="label">申请人：</label>
                              <div class="content">中国</div>
                            </div>
                            <div class="information-item">
                              <label class="label">公开日：</label>
                              <div class="content">2012.08.12</div>
                            </div>
                            <div class="information-item">
                              <label class="label">公开号：</label>
                              <div class="content">CN123123444</div>
                            </div>
                            <div class="information-item">
                              <label class="label">法律状态：</label>
                              <div class="content">无效</div>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="box border">
                      <div class="box-header">
                        摘要
                      </div>
                      <div class="box-body abs">
                        <el-scrollbar style="height: 100%;overflow: hidden;">
                          <div class="inner">
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                          </div>
                        </el-scrollbar>
                      </div>
                    </div>
                  </div>
                  <div class="patent-content">
                    <h5 class="title contrast">对比文献标题:紧急呼叫处理</h5>
                    <div class="box">
                      <div class="box-header">
                        著录项目
                      </div>
                      <div class="box-body">
                        <div class="inner">
                          <div class="information">
                            <div class="information-item">
                              <label class="label">申请号：</label>
                              <div class="content">CN123444</div>
                            </div>
                            <div class="information-item">
                              <label class="label">申请人：</label>
                              <div class="content">中国</div>
                            </div>
                            <div class="information-item">
                              <label class="label">公开日：</label>
                              <div class="content">2012.08.12</div>
                            </div>
                            <div class="information-item">
                              <label class="label">公开号：</label>
                              <div class="content">CN123123444</div>
                            </div>
                            <div class="information-item">
                              <label class="label">法律状态：</label>
                              <div class="content">无效</div>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="box border">
                      <div class="box-header">
                        摘要
                      </div>
                      <div class="box-body abs">
                        <el-scrollbar style="height: 100%;overflow: hidden;">
                          <div class="inner">
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                          </div>
                        </el-scrollbar>
                      </div>
                    </div>
                  </div>
                </div>
              </el-tab-pane>
              <el-tab-pane label="说明书" name="desc">
                <div class="patent-wrapper clearfix">
                  <div class="patent-content">
                    <h5 class="title origin">原文献标题:手机历史app的管理方法及系统</h5>
                    <div class="box border">
                      <div class="box-header">
                        说明书
                      </div>
                      <div class="box-body desc">
                        <el-scrollbar style="height: 100%;overflow: hidden;">
                          <div class="inner">
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                          </div>
                        </el-scrollbar>
                      </div>
                    </div>
                  </div>
                  <div class="patent-content">
                    <h5 class="title contrast">对比文献标题:紧急呼叫处理</h5>
                    <div class="box">
                      <div class="box-header">
                        说明书
                      </div>
                      <div class="box-body desc">
                        <el-scrollbar style="height: 100%;overflow: hidden;">
                          <div class="inner">
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                          </div>
                        </el-scrollbar>
                      </div>
                    </div>
                  </div>
                </div>
              </el-tab-pane>
              <el-tab-pane label="权利要求" name="claim">
                <div class="patent-wrapper clearfix">
                  <div class="patent-content">
                    <h5 class="title origin">原文献标题:手机历史app的管理方法及系统</h5>
                    <div class="box border">
                      <div class="box-header">
                        权利要求
                      </div>
                      <div class="box-body claim">
                        <el-scrollbar style="height: 100%;overflow: hidden;">
                          <div class="inner">
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                          </div>
                        </el-scrollbar>
                      </div>
                    </div>
                  </div>
                  <div class="patent-content">
                    <h5 class="title contrast">对比文献标题:紧急呼叫处理</h5>
                    <div class="box">
                      <div class="box-header">
                        权利要求
                      </div>
                      <div class="box-body claim">
                        <el-scrollbar style="height: 100%;overflow: hidden;">
                          <div class="inner">
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                            <p>作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</p>
                            <p>该委员会还修改了其规则，旨在限制司机在曼哈顿96号街以下地区无乘客驾驶情况下的巡航时间的规则。根据新规定，Uber和Lyft必须将无乘客驾驶时间从41%减少到31%。Uber在新诉讼中挑战了这两个规则。该法规是在2月份颁布的新的最低工资规则以及所有租用车辆和黄色出租车的拥堵费的基础上制定的。</p>
                          </div>
                        </el-scrollbar>
                      </div>
                    </div>
                  </div>
                </div>
              </el-tab-pane>
            </el-tabs>
          </div>
        </div>
      </div>
      <div class="contrast-view">
        <el-dialog title="对比库文件管理" :visible.sync="dialogTableVisible">
          <table cellspacing="0" cellpadding="0" border="0" class="table border table-info">
            <thead>
            <tr>
              <th style="width: 6%">
                <div class="cell">序号</div>
              </th>
              <th style="width: 12%">
                <div class="cell">公开号</div>
              </th>
              <th style="width: 20%">
                <div class="cell">文献标题</div>
              </th>
              <th style="width: 12%">
                <div class="cell">公开日</div>
              </th>
              <th style="width: 12%">
                <div class="cell">申请号</div>
              </th>
              <th style="width: 10%">
                <div class="cell">申请人</div>
              </th>
              <th style="width: 10%">
                <div class="cell">IPC分类</div>
              </th>
              <th>
                <div class="cell">操作</div>
              </th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="(item ,index) in contrastList" :key="index">
              <td class="center">
                <div class="cell"><span class="circle">{{index +1}}</span></div>
              </td>
              <td>
                <div class="cell">{{item.pa}}</div>
              </td>
              <td>
                <div class="cell">{{item.title}}</div>
              </td>
              <td class="center">
                <div class="cell">{{item.pd}}</div>
              </td>
              <td class="center">
                <div class="cell">{{item.an}}</div>
              </td>
              <td>
                <div class="cell">{{item.applications}}</div>
              </td>
              <td>
                <div class="cell">{{item.ipc}}</div>
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
          <div class="contrast-paging">
            <el-pagination
              @size-change="handleSizeChange"
              @current-change="handleCurrentChange"
              :current-page.sync="currentPage3"
              :page-size="100"
              layout="prev, pager, next, jumper"
              :total="1000">
            </el-pagination>
          </div>
        </el-dialog>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      contrastList: [{
        pa: '1212121212',
        title: '手机外屏历史管理装置及方法',
        pd: '2018-10-23',
        an: '3023434344',
        applications: '张三',
        ipc:'G01011'
      }, {
        pa: '1212121212',
        title: '数据回收方法及移动端',
        pd: '2018-10-23',
        an: '3023434344',
        applications: '张三',
        ipc:'G01011'
      },{
        pa: '1212121212',
        title: '一种移动终端的数据处理方法及系统',
        pd: '2018-10-23',
        an: '3023434344',
        applications: '张三',
        ipc:'G01011'
      },{
        pa: '1212121212',
        title: '一种浏览历史的查询方法',
        pd: '2018-10-23',
        an: '3023434344',
        applications: '张三',
        ipc:'G01011'
      }],
      dialogTableVisible: false,
      patents: [{
        ap: 'CN123123',
        name: '无线通信网络中的信号干扰测量信号干扰测量',
        score: 90
      },{
        ap: 'CN123123',
        name: '无线通信网络中的信号干信号干扰测量量',
        score: 80
      },{
        ap: 'CN123123',
        name: '无线通信网络',
        score: 67
      },{
        ap: 'CN123123',
        name: '无线通信网络中的信号干扰测量',
        score: 48
      },{
        ap: 'CN123123',
        name: '无线通信网络中的信号干扰测量',
        score: 44
      },{
        ap: 'CN123123',
        name: '无线通信网络中的信号',
        score: 41
      },{
        ap: 'CN123123',
        name: '无线通信网络中的信号干扰测量',
        score: 22
      },{
        ap: 'CN123123',
        name: '无线通信网络中的信号干扰测量',
        score: 21
      },{
        ap: 'CN123123',
        name: '无线通信网络中的信号干扰测量',
        score: 19
      },{
        ap: 'CN123123',
        name: '无线通信网络中的信号干扰测量',
        score: 2
      }],
      activeName: 'abs'
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
  .patent-content{
    color: rgb(68, 68, 69);
    float: left;
    width: 50%;
    box-sizing: border-box;
    .title{
      text-align: center;
      font-size: 15px;
      padding: 10px 20px;
      box-sizing: border-box;
      width: 100%;
      text-overflow: ellipsis;
      overflow: hidden;
      white-space: nowrap;
      margin: 0;
      &.origin{
        color: rgb(67, 100, 216);
      }
      &.contrast{
        color: rgb(243, 108, 124);
      }
    }
    .box{
      box-sizing: border-box;
      &.border{
        border-right: 1px solid rgb(232, 239, 250);
      }
      .box-header{
        line-height: 40px;
        padding: 0 10px;
        background-color: rgb(243, 247, 253);
        font-size: 14px;
      }
      .box-body{
        min-height: 200px;
        & .inner{
          padding: 10px;
        }
        & p{
          margin: 0;
          line-height: 25px;
          font-size: 14px;
          text-indent: 28px;
        }
        &.abs{
          height: 462px;
        }
        &.desc{
          height: 700px;
        }
        &.claim{
          height: 700px;
        }
      }
    }
  }
  .right .panel .panel-body.no-padding{
    padding: 5px 0 0 0;
  }
  .information .information-item{
    margin-bottom: 20px;
  }
  .contrast-paging{
    text-align: right;
    margin-top:30px;
    margin-right: 20px;
  }
</style>
