<template>
  <div class="app-container">
    <div>
      <div class="panel">
        <div class="panel-header clearfix">
          <div class="start">
            <h4 class="title">基本信息</h4>
          </div>
          <div class="end">
            <span class="text">本报告基于xx版本库</span>
          </div>
        </div>
        <div class="panel-body preview-body">
          <el-row>
            <el-col :span="12">
              <div class="grid-content bg-purple">
                <div class="information">
                  <div class="information-item">
                    <label class="label">申请人：</label>
                    <div class="content">{{baseInfo.applicant}}</div>
                  </div>
                </div>
              </div>
            </el-col>
            <el-col :span="12">
              <div class="grid-content bg-purple-light">
                <div class="information">
                  <div class="information-item">
                    <label class="label">说明书段数：</label>
                    <div class="content number">{{baseInfo.descCount}}</div>
                  </div>
                </div>
              </div>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="12">
              <div class="grid-content bg-purple">
                <div class="information">
                  <div class="information-item">
                    <label class="label">检测时间：</label>
                    <div class="content">{{baseInfo.checkTime}}</div>
                  </div>
                </div>
              </div>
            </el-col>
            <el-col :span="12">
              <div class="grid-content bg-purple-light">
                <div class="information">
                  <div class="information-item">
                    <label class="label">权利要求段数：</label>
                    <div class="content number">{{baseInfo.claimCount}}</div>
                  </div>
                </div>
              </div>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="24">
              <div class="grid-content bg-purple-dark">
                <div class="information">
                  <div class="information-item">
                    <label class="label">结论：</label>
                    <div class="content">
                      <el-input
                        type="textarea"
                        :rows="5"
                        placeholder="请输入内容"
                        v-model="baseInfo.conclusion">
                      </el-input>
                    </div>
                  </div>
                </div>
              </div>
            </el-col>
          </el-row>
        </div>
      </div>
    </div>
    <div>
      <el-row :gutter="20">
        <el-col :span="16">
          <div class="panel">
            <div class="panel-header clearfix">
              <div class="start">
                <h4 class="title">对比文献列表</h4>
              </div>
              <div class="end">
                <button type="button" class="btn btn-danger">
                  <i class="el-icon-delete"></i>
                  删除
                </button>
              </div>
            </div>
            <div class="panel-body no-padding compare-body">
              <div class="grid-content bg-purple">
                <table cellspacing="0" cellpadding="0" border="0" class="table stripe">
                  <thead>
                  <tr>
                    <th style="width: 7%">
                      <div class="cell">
                        <el-checkbox :indeterminate="true" v-model="checked1"></el-checkbox>
                      </div>
                    </th>
                    <th style="width: 8%">
                      <div class="cell">序号</div>
                    </th>
                    <th style="width: 15%">
                      <div class="cell">文献号</div>
                    </th>
                    <th style="width: 10%">
                      <div class="cell">类别</div>
                    </th>
                    <th style="width: 15%">
                      <div class="cell">公开号</div>
                    </th>
                    <th style="width: 15%">
                      <div class="cell">相关段落</div>
                    </th>
                    <th style="width: 15%">
                      <div class="cell">涉及权利要求</div>
                    </th>
                    <th style="width: 15%">
                      <div class="cell">IPC分类号</div>
                    </th>
                    <th style="width: 10%">
                      <div class="cell">相似度</div>
                    </th>
                  </tr>
                  </thead>
                  <tbody v-for="(item,index) in compareList" :key="index">
                  <tr>
                    <td class="center">
                      <div class="cell">
                        <el-checkbox v-model="checked2"></el-checkbox>
                      </div>
                    </td>
                    <td class="center">
                      <div class="cell">
                        <span class="circle">{{index+1}}</span>
                      </div>
                    </td>
                    <td>
                      <div class="cell">{{item.docNumber}}</div>
                    </td>
                    <td>
                      <div class="cell">{{item.category}}</div>
                    </td>
                    <td>
                      <div class="cell">{{item.openDay}}</div>
                    </td>
                    <td>
                      <div class="cell">{{item.paragraph}}</div>
                    </td>
                    <td>
                      <div class="cell">{{item.claim}}</div>
                    </td>
                    <td>
                      <div class="cell">{{item.ipc}}</div>
                    </td>
                    <td>
                      <div class="cell">
                        <span :class="[item.score > 50 ? 'high' : 'low']">{{item.score + '%'}}</span>
                      </div>
                    </td>
                  </tr>
                  </tbody>
                </table>
              </div>
            </div>
            <div class="panel-footer center">
              <div class="save-report-btn">
                <button type="button" class="btn btn-primary">保存报告</button>
              </div>
            </div>
          </div>
        </el-col>
        <el-col :span="8">
          <div class="panel alternative">
            <div class="panel-header clearfix">
              <div class="start">
                <h4 class="title">备选文献库(双击添加)</h4>
              </div>
            </div>
            <div class="panel-body alternative-body no-padding">
              <ul v-for="(item,index) in alternativeList" :key="index">
                <li>
                  <p><span class="">{{item.docNumber}}</span><span>{{item.category}}</span><span>{{item.openDay}}</span></p>
                  <p><span>{{item.title}}</span></p>
                  <p><span>{{item.ipc}}</span></p>
                </li>
              </ul>
            </div>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      baseInfo:{
        applicant: '乐金电子(中国)研究开发中心有限公司',
        descCount: 3,
        checkTime: '2089-10-20',
        claimCount: 4,
        conclusion:''
      },
      compareList:[
        {docNumber:'20134343434',category:'B',openDay:'2020223',paragraph:'说明书第一段',claim:'权利要求1',ipc:'DHODDD',score:90},
        {docNumber:'20134343434',category:'B',openDay:'2020223',paragraph:'说明书第一段',claim:'权利要求1',ipc:'DHODDD',score:78},
        {docNumber:'20134343434',category:'B',openDay:'2020223',paragraph:'说明书第一段',claim:'权利要求1',ipc:'DHODDD',score:34},
        {docNumber:'20134343434',category:'B',openDay:'2020223',paragraph:'说明书第一段',claim:'权利要求1',ipc:'DHODDD',score:45},
        {docNumber:'20134343434',category:'B',openDay:'2020223',paragraph:'说明书第一段',claim:'权利要求1',ipc:'DHODDD',score:45},
        {docNumber:'20134343434',category:'B',openDay:'2020223',paragraph:'说明书第一段',claim:'权利要求1',ipc:'DHODDD',score:45}
      ],
      alternativeList:[
        {docNumber:'20134343434',category:'B',openDay:'2020223',paragraph:'说明书第一段',claim:'权利要求1',ipc:'DHODDD',score:90,title:'历史记录信息的清除方法'},
        {docNumber:'20134343434',category:'B',openDay:'2020223',paragraph:'说明书第一段',claim:'权利要求1',ipc:'DHODDD',score:90,title:'历史记录信息的清除方法'},
        {docNumber:'20134343434',category:'B',openDay:'2020223',paragraph:'说明书第一段',claim:'权利要求1',ipc:'DHODDD',score:90,title:'历史记录信息的清除方法'}
      ]
    }
  },
  methods: {}
}
</script>
<style scoped lang="scss">
$labelWidth: 150px;
.information .information-item .label{
    width: $labelWidth;
}
.information .information-item .content{
  margin-left: $labelWidth + 5px;
}
.preview-body{
    padding: 20px;
}
.compare .header .tools{
  display: inline-block;
  float: right;
}
.save-report-btn{
    text-align: center;
}
.alternative-body ul{
  margin:0px;
  padding:0px;
  color: #3a3a3a;
  font-size: 14px;
}
.alternative-body ul li {
  list-style: none;
  padding:5px 10px;
  border-bottom: 1px solid #E0E9FC;
  cursor: pointer;
}
.alternative-body ul li p{
  margin:10px;
  padding:0;
}
.alternative-body ul li span{
  margin-right:10px;
}
.information .information-item{
  font-size: 15px;
}
.panel.alternative .panel-header{
  background-color: #1B95DE;
}
.save-report-btn{
  margin-top:30px;
  margin-bottom:20px;
}
</style>
