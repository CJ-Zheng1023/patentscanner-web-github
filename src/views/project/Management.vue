<template>
  <div class="app-container project-management">
    <div class="list">
      <div class="panel">
        <div class="panel-header">
          <div class="start">
            <div class="title">工程列表</div>
          </div>
          <div class="end">
            <div class="form">
              <el-form :inline="true" :model="formInline" class="demo-form-inline">
                <el-form-item>
                  <el-input prefix-icon="el-icon-search" v-model="formInline.name" placeholder="请输入工程名称"></el-input>
                </el-form-item>
                <el-form-item>
                  <el-select v-model="formInline.status" placeholder="执行状态">
                    <el-option label="完成" value="1"></el-option>
                    <el-option label="暂停" value="2"></el-option>
                  </el-select>
                </el-form-item>
              </el-form>
            </div>
            <div class="btn-group" style="line-height: 1">
              <button type="button" class="btn btn-primary">搜 索</button>
              <button type="button" class="btn btn-danger">重 置</button>
              <button type="button" class="btn">新 建</button>
            </div>
          </div>
        </div>
        <div class="panel-body">
          <el-row :gutter="10">
            <el-col :span="6">
              <div class="grid-content">
                <i class="iconfont miit-icon-close close"></i>
                <div class="title">一批次专利检测</div>
                <div class="status"><span class="circle"><i class="iconfont miit-icon-check"></i></span><span class="text">已完成</span></div>
                <div class="progress">
                  <el-progress :show-text="false" :percentage="percentage" :color="customColor"></el-progress>
                </div>
                <div class="date">创建日期: 2012.02.02</div>
              </div>
            </el-col>
            <el-col :span="6">
              <div class="grid-content">
                <i class="iconfont miit-icon-close close"></i>
                <div class="title">二批次专利检测</div>
                <div class="status"><span class="circle"><i class="iconfont miit-icon-running"></i></span><span class="text">已扫描:20%</span></div>
                <div class="progress">
                  <el-progress :show-text="false" :percentage="percentage" :color="customColor"></el-progress>
                  <i class="iconfont miit-icon-pause"></i>
                </div>
                <div class="date">创建日期: 2012.02.02</div>
              </div>
            </el-col>
            <el-col :span="6">
              <div class="grid-content">
                <i class="iconfont miit-icon-close close"></i>
                <div class="title">三批次专利检测</div>
                <div class="status"><span class="circle"><i class="iconfont miit-icon-pause"></i></span><span class="text">已暂停</span></div>
                <div class="progress">
                  <el-progress :show-text="false" :percentage="percentage" :color="customColor"></el-progress>
                  <i class="iconfont miit-icon-play play"></i>
                </div>
                <div class="date">创建日期: 2012.02.02</div>
              </div>
            </el-col>
            <el-col :span="6">
              <div class="grid-content">
                <i class="iconfont miit-icon-close close"></i>
                <div class="title">四批次专利检测</div>
                <div class="status"><span class="circle"><i class="iconfont miit-icon-wait"></i></span><span class="text">等待扫描</span></div>
                <div class="progress">
                  <el-progress :show-text="false" :percentage="percentage" :color="customColor"></el-progress>
                </div>
                <div class="date">创建日期: 2012.02.02</div>
              </div>
            </el-col>
          </el-row>
          <div class="arrow prev"><i class="el-icon-arrow-left"></i></div>
          <div class="arrow next"><i class="el-icon-arrow-right"></i></div>
        </div>
      </div>
    </div>
    <div class="info">
      <el-row :gutter="2">
        <el-col :span="12">
          <div class="panel panel-info">
            <div class="panel-header">
              <div class="start">
                <div class="title">工程名称</div>
              </div>
            </div>
            <div class="panel-body">
              <div class="name">红芯浏览器检测</div>
            </div>
          </div>
        </el-col>
        <el-col :span="12">
          <div class="panel panel-info">
            <div class="panel-header">
              <div class="start">
                <div class="title">工程描述</div>
              </div>
            </div>
            <div class="panel-body">
              <div class="description">作为目前美国网约车平台的第一大巨头，近几个月时间里，优步（uber）也是诸事不顺了。因为纽约市政府的新规定，导致网约车数量减少打车变得更难了！日前，uber再次起诉了纽约市，据悉这也是其今年第二次起诉纽约市了。Uber最新消息Uber最新消息据外媒TheVerge报道，Uber周五对纽约市提起诉讼，以推翻限制打车服务司机在城市繁忙地区度过的时间的规定。这是Uber今年第二次起诉纽约市。一个多月前纽约市出租车和豪华轿车委员会（TLC）投票决定，延长对允许在纽约市运营的Uber和Lyft车辆数量的时间上限。现在暂停新车牌照的期限延长至2020年8月。</div>
            </div>
          </div>
        </el-col>
        <el-col :span="12">
          <div class="panel panel-info">
            <div class="panel-header">
              <div class="start">
                <div class="title">结果分布</div>
              </div>
            </div>
            <div class="panel-body charts">
              <ve-pie :data="chartData1"></ve-pie>
            </div>
          </div>
        </el-col>
        <el-col :span="12">
          <div class="panel panel-info">
            <div class="panel-header">
              <div class="start">
                <div class="title">类型分布</div>
              </div>
            </div>
            <div class="panel-body charts">
              <ve-pie :data="chartData2" :colors="colors"></ve-pie>
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
      formInline: {
        name: '',
        status: ''
      },
      percentage: 20,
      customColor: '#fff',
      chartData1: {
        columns: ['类型', '数量'],
        rows: [
          { '类型': '侵权', '数量': 150 },
          { '类型': '未侵权', '数量': 204 },
          { '类型': '疑似侵权', '数量': 127 }
        ]
      },
      chartData2: {
        columns: ['类型', '数量'],
        rows: [
          { '类型': '外观', '数量': 51 },
          { '类型': '实用新型', '数量': 101 },
          { '类型': '发明', '数量': 321 }
        ],
      },
      colors: ['rgb(107, 225, 227)', 'rgb(253, 219, 101)', 'rgb(253, 157, 128)']
    }
  }
}
</script>
<style scoped lang="scss">
  .el-form-item{
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form{
    display: inline-block;
    margin-right: 15px;
  }
  .list .panel-body{
    color: #fff;
    background-color: #3053cc;
    border-top-left-radius: 0;
    border-top-right-radius: 0;
    padding: 15px 35px;
    position: relative;
    & .arrow{
      background-color: rgb(94, 130, 248);
      height: 26px;
      width: 26px;
      border-radius: 50%;
      line-height: 26px;
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      color: #fff;
      font-size: 16px;
      text-align: center;
      cursor: pointer;
      &.prev{
        left: 5px;
      }
      &.next{
        right: 5px;
      }
    }
  }
  .grid-content{
    position: relative;
    background-color: rgb(94, 130, 248);
    border-radius: 2px;
    padding: 18px 22px;
    & .close{
      position: absolute;
      right: 3px;
      top: 3px;
      cursor: pointer;
    }
    & .title{
      font-size: 15px;
      font-weight: bold;
      text-align: center;
      margin-bottom: 13px;
    }
    $circleSize: 20px;
    & .status{
      font-size: 14px;
      text-align: center;
      & .circle{
        background-color: #fff;
        color: rgb(100, 135, 248);
        display: inline-block;
        width: $circleSize;
        height: $circleSize;
        border-radius: 50%;
        vertical-align: middle;
        text-align: center;
        line-height: $circleSize;
      }
      & .text{
        margin-left: 4px;
        display: inline-block;
        vertical-align: middle;
      }
    }
    & .progress{
      padding: 10px 30px 10px 0;
      position: relative;
      & .iconfont{
        position: absolute;
        right: -5px;
        top: 50%;
        transform: translateY(-50%);
        color: #fff;
        font-size: 20px;
        font-weight: bolder;
        cursor: pointer;
        &.play{
          font-size: 16px;
        }
      }
    }
    & .date{
      font-size: 13px;
    }
  }
  .info .panel{
    margin-bottom: 2px;
  }
  .info .panel-header{
    background-color: #d6e1fa;
    color: rgb(61, 61, 61);
    line-height: 40px;
    height: 40px;
  }
  .info .panel-body{
    height: 180px;
    color: rgb(61, 61, 61);
    &.charts{
      height: auto;
    }
    & .name{
      font-size: 25px;
      text-align: center;
      margin-top: 45px;
    }
    & .description{
      font-size: 14px;
      line-height: 20px;
      text-indent: 28px;
    }
  }
</style>
