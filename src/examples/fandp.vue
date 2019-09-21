<template>
  <div class="app-container">
    <button type="button" class="btn">深蓝色</button>
    <button type="button" class="btn btn-primary">蓝色</button>
    <button type="button" class="btn btn-info">浅蓝色</button>
    <button type="button" class="btn btn-normal">灰色</button>
    <button type="button" class="btn btn-warn">橙色</button>
    <button type="button" class="btn btn-danger">红色</button>
    <p>按钮尺寸</p>
    <button type="button" class="btn btn-primary btn-lg">大型按钮</button>
    <button type="button" class="btn btn-primary">原始按钮</button>
    <button type="button" class="btn btn-primary btn-sm">小型按钮</button>
    <button type="button" class="btn btn-primary btn-xs">迷你按钮</button>
    <p>圆角按钮</p>
    <button type="button" class="btn btn-primary btn-radis">蓝色按钮</button>
    <p>朴素按钮</p>
    <button type="button" class="btn btn-primary is-plain">蓝色按钮</button>
    <button type="button" class="btn is-plain">深蓝色按钮</button>
    <button type="button" class="btn btn-danger is-plain">红色按钮</button>
    <button type="button" class="btn btn-primary is-plain btn-radis">蓝色按钮</button>
    <button type="button" class="btn btn-primary is-plain btn-radis btn-xs">查看</button>
    <button type="button" class="btn btn-danger is-plain btn-radis btn-xs">删除</button>

    <p>按钮组</p>
    <div class="btn-group">
      <button type="button" class="btn btn-primary ">蓝色</button>
      <button type="button" class="btn btn-info">浅蓝色</button>
    </div>

    <p>图标按钮</p>
    <button type="button" class="btn btn-danger is-plain btn-radis btn-xs btn-icon">
      <i class="el-icon-delete"></i>
      删 除
    </button>

    <button type="button" class="btn btn-icon">
      <img src="@/assets/images/delete.png">
      图标
    </button>

  </div>
</template>
