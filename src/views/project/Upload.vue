<template>
  <div class="app-container upload">
    <div class="panel">
      <div class="panel-header clearfix">
        <div class="start">
          <h4 class="title">上传扫描</h4>
        </div>
      </div>
      <div class="panel-body">
        <div class="update-body">
          <div class="handmovement">
            <el-upload
              class="upload-demo"
              action="https://jsonplaceholder.typicode.com/posts/"
              :on-preview="handlePreview"
              :on-remove="handleRemove"
              :before-remove="beforeRemove"
              multiple
              :limit="3"
              :on-exceed="handleExceed"
              :file-list="fileList">
              <button type="button" class="btn btn-normal btn-icon"><i class="el-icon-upload2"></i>点击上传</button><span class="update-desc">（ 可直接拖动列表 ）</span>
            </el-upload>
          </div>
          <div class="dragmovement">
            <el-upload
              class="upload-demo"
              drag
              action="https://jsonplaceholder.typicode.com/posts/"
              multiple>
              <i class="el-icon-upload"></i>
              <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
            </el-upload>
            <button type="button" class="btn btn-primary hand-btn">上  传 文 件</button>
          </div>
        </div>
        <div class="file-list">
          <table cellspacing="0" cellpadding="0" border="0" class="table border table-info stripe">
            <thead>
            <tr>
              <th style="width: 10%">
                <div class="cell">序号</div>
              </th>
              <th style="width: 60%">
                <div class="cell">发明名称</div>
              </th>
              <th style="width: 30%">
                <div class="cell">进度</div>
              </th>
            </tr>
            </thead>
            <tbody>
            <tr  v-for="(item,index) in patentFileList" :key="index">
              <td class="center">
                <div class="cell"><span class="circle">{{index +1}}</span></div>
              </td>
              <td>
                <div class="cell">{{item.name}}</div>
              </td>
              <td>
                <div class="cell"><el-progress :percentage=item.process :color="customColor"></el-progress></div>
              </td>
            </tr>
            </tbody>
          </table>
          <div class="paging">
            <el-pagination :current-page.sync="currentPage" :page-size="100" layout="prev, pager, next, jumper" :total="1000"></el-pagination>
          </div>
        </div>
        <div class="scan-process">
          <div class="scan-body">
            <div class="left-title">检测进度</div>
            <div class="detail">
              <p><span>当前扫描专利500件, </span><span>已扫描专利100件，</span><span>未扫描专利400件</span></p>
              <p><el-progress :percentage="50"></el-progress></p>
              <p><span>已扫描8分钟, </span><span>还需要4分钟, </span><span>请耐心等待</span></p>
            </div>
          </div>
        </div>
      </div>
      <div class="panel-footer center">
        <button type="button" class="btn">开始扫描</button>
        <button type="button" class="btn btn-primary">暂停扫描</button>
        <button type="button" class="btn btn-danger">取消扫描</button>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        patentFileList:[
          {name:'基于移动互联网的景区自助旅游系统',process:90},
          {name:'紧急呼叫系统',process:80},
          {name:'基于移动互联网的景区自助旅游系统',process:60},
          {name:'基于移动互联网的景区自助旅游系统',process:50},
          {name:'基于移动互联网的景区自助旅游系统',process:20},
          {name:'基于移动互联网的景区自助旅游系统',process:0}

        ],
        customColor:'#2D85FD'
      }
    }
  }
</script>
<style scoped lang="scss">
.upload .update-body{
  padding: 30px 10px;
  width: 900px;
  margin: 0 auto;
}
.upload .update-body .update-desc{
  margin-left: 20px;
  color: #606266;
  font-size:15px;
}
.upload .handmovement{
  margin-bottom: 30px;
}
.upload .btn-normal:hover {
  border-color: #409EFF;
}
.upload .hand-btn{
  vertical-align: top;
  margin-left: 30px;
}
.upload .paging{
  margin-top: 20px;
  margin-bottom: 20px;
  text-align: right;
}
.scan-body{
  position: relative;
}
.scan-body .left-title{
  position: absolute;
  left: 10%;
  top:50%;
  transform:translate(-10%,-50%);
  display: inline-block;
}
.scan-body .detail{
  display: inline-block;
  width:80%;
  padding-left: 20%;
}
.scan-process{
  color: #606266;
  font-size:14px;
  margin-bottom: 20px;
}

</style>
