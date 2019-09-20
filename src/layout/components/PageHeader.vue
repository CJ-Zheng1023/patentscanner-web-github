<template>
  <div class="page-header">
    <div class="logo">
      <img src="@/assets/images/logo.png"/>
      <span class="brand">专利扫描平台</span>
    </div>
    <div class="topbar">
      <span class="text">李思</span>
      <span class="text">欢迎登录</span>
      <a href="javascript:;" class="btn">注销登录</a>
    </div>
  </div>
</template>
<style scoped lang="scss">
  @import "~@/styles/variables.scss";
  .page-header{
    height: $pageHeaderHeight;
    position: fixed;
    box-sizing: border-box;
    padding: 0 60px;
    left: 0;
    top: 0;
    width: 100%;
    z-index: 88;
    background-image: url("~@/assets/images/banner.png");
    background-size: cover;
    & .logo{
      float: left;
      line-height: $pageHeaderHeight;
      & img{
        vertical-align: middle;
      }
      & .brand{
        font-size: 30px;
        color: #fff;
        vertical-align: middle;
      }
    }
    & .topbar{
      float: right;
      line-height: $pageHeaderHeight;
      & .text, & .btn{
        color: #fff;
        font-size: 14px;
        margin: 0 5px;
        vertical-align: middle;
      }
    }
  }
</style>
