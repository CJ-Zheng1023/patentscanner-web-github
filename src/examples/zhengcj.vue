<template>
  <div class="app-container">
    <h3>panel</h3>
    <div class="panel">
      <div class="panel-header clearfix">
        <div class="start">
          <h4 class="title">标题</h4>
        </div>
        <div class="end">
          <span class="text">本报告基于xx版本库</span>
        </div>
      </div>
      <div class="panel-body">内容展示区</div>
      <div class="panel-footer center">分页</div>
    </div>
    <div class="panel panel-info">
      <div class="panel-header clearfix">
        <div class="start">
          <div class="menubar">
            <ul class="menus clearfix">
              <li class="menu-item">
                <a hre="javascript:;">添加至对比库</a>
              </li>
              <li class="menu-item">
                <a hre="javascript:;">添加至对比库</a>
              </li>
              <li class="menu-item">
                <a hre="javascript:;">添加至对比库</a>
              </li>
            </ul>
          </div>
        </div>
        <div class="end">
          <span class="text">本报告基于xx版本库</span>
        </div>
      </div>
      <div class="panel-body">内容展示区</div>
      <div class="panel-footer right">分页</div>
    </div>
    <h3>information</h3>
    <div class="panel">
      <div class="panel-body">
        <div class="information">
          <div class="information-item">
            <label class="label">label：</label>
            <div class="content">content</div>
          </div>
          <div class="information-item">
            <label class="label">label：</label>
            <div class="content number">3</div>
          </div>
        </div>
      </div>
    </div>
    <h3>table</h3>
    <div class="panel">
      <div class="panel-body">
        <table cellspacing="0" cellpadding="0" border="0" class="table table-primary stripe">
          <thead>
            <tr>
              <th style="width: 80px">
                <div class="cell">序号</div>
              </th>
              <th style="width: 150px">
                <div class="cell">列1</div>
              </th>
              <th style="width: 200px">
                <div class="cell">列2</div>
              </th>
              <th>
                <div class="cell">操作</div>
              </th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td class="center">
                <div class="cell">1</div>
              </td>
              <td>
                <div class="cell">name</div>
              </td>
              <td>
                <div class="cell">asdfasdlfjalsdfjladflakdflajsdflajdlf</div>
              </td>
              <td class="center">
                <div class="cell"></div>
              </td>
            </tr>
            <tr class="active">
              <td class="center">
                <div class="cell">
                  <span class="circle">2</span>
                </div>
              </td>
              <td>
                <div class="cell">name</div>
              </td>
              <td>
                <div class="cell">asdfasdlfjalsdfjladflakdflajsdflajdlf</div>
              </td>
              <td class="center">
                <div class="cell"></div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <div class="panel">
      <div class="panel-body">
        <table cellspacing="0" cellpadding="0" border="0" class="table table-info">
          <thead>
          <tr>
            <th style="width: 50px">
              <div class="cell">
                <el-checkbox :indeterminate="true" v-model="checked1"></el-checkbox>
              </div>
            </th>
            <th style="width: 80px">
              <div class="cell">序号</div>
            </th>
            <th style="width: 150px">
              <div class="cell">列1</div>
            </th>
            <th style="width: 200px">
              <div class="cell">列2</div>
            </th>
            <th>
              <div class="cell">操作</div>
            </th>
          </tr>
          </thead>
          <tbody>
          <tr>
            <td class="center">
              <div class="cell">
                <el-checkbox v-model="checked2"></el-checkbox>
              </div>
            </td>
            <td class="center">
              <div class="cell">1</div>
            </td>
            <td>
              <div class="cell">name</div>
            </td>
            <td>
              <div class="cell">asdfasdlfjalsdfjladflakdflajsdflajdlf</div>
            </td>
            <td class="center">
              <div class="cell"></div>
            </td>
          </tr>
          <tr>
            <td class="center">
              <div class="cell">
                <el-checkbox v-model="checked3"></el-checkbox>
              </div>
            </td>
            <td class="center">
              <div class="cell">
                <span class="circle">2</span>
              </div>
            </td>
            <td>
              <div class="cell">name</div>
            </td>
            <td>
              <div class="cell">asdfasdlfjalsdfjladflakdflajsdflajdlf</div>
            </td>
            <td class="center">
              <div class="cell"></div>
            </td>
          </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      checked1: false,
      checked2: false,
      checked3: false
    }
  }
}
</script>
