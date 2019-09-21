<template>
  <div class="login-container">
    <div class="login-header">
       <div class="logo">
         <img src="~@/assets/images/logo.png">
         <span class="title">专利扫描平台</span>
       </div>
       <div class="desc"><span>让伪自主无处可藏，助力中国国产自主化进程</span></div>
    </div>
    <div class="login-form">
      <el-form :model="form" >
        <div class="title"><span>用户登录</span></div>
        <el-form-item>
          <el-input  placeholder="请输入用户名"  v-model="form.username">
            <img slot="prefix" class="" src="~@/assets/images/username.png" />
          </el-input>
        </el-form-item>
        <el-form-item>
          <el-input  placeholder="请输入密码" v-model="form.password">
            <img slot="prefix" class="" src="~@/assets/images/password.png" />
          </el-input>
        </el-form-item>
        <button type="button" class="btn btn-primary login-btn">登录</button>
        <div class="footer">
          <div class="remember-me">
            <el-checkbox v-model="form.rememberpass">记住密码</el-checkbox>
          </div>
          <div class="regist">
            注册账号
          </div>
        </div>
      </el-form>
    </div>
    <div class="login-footer">
      <!-- <p>
         当前软件开源技术已经成为驱动技术发展的关键动力，但是开源不等于自由，开源不等于知识产权自主可控；知识产权自由可控，首先是自主，才能达到真正的可控，进而实现全面安全，不受制于人，自主是可控的必要条件。目前很多计算机软件产品的自主国产化还停留在以国外核心技术为基础，进行外层封装的一种准自主化或伪自主化。
         这种‘有质无量’的国产化会阻碍我国自主化的战略进程。
      </p>
      <p>
        东软结合在知识产权领域十年的积累和研究，基于人工智能AI技术和大数据技术构建
      </p> -->
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      form: {
        username: '',
        password: '',
        rememberpass: ''
      }
    }
  }
}
</script>
<style  scoped>
  .login-container{
    position: relative;
    background-image: url("~@/assets/images/login_back.png");
    background-repeat: no-repeat;
    background-size: cover;
    height:100%;
  }
  .login-header{
    position: absolute;
    left:80px;
    top:50px;
    padding:5px 10px;
  }
  .login-header .logo{
    display:inline-block;
    margin-right: 40px;
  }
  .login-header .logo img{
    vertical-align: middle;
    margin-right: 10px;
  }
  .login-header .logo .title{
    vertical-align: middle;
    font-size: 28px;
    color: #FFF;
    font-weight: 500;
  }
  .login-header .desc{
    display:inline-block;
    color: #FFF;
    font-size: 15px;
    vertical-align: middle;
  }
  .login-form{
    background-color: rgb(224,235,255);
    position: absolute;
    right: 110px;
    top:170px;
    padding: 20px 60px 33px 60px;
    width: 451px;
  }
  .login-form .title{
    color:rgb(97,155,209);
    font-size: 30px;
    font-weight: 400;
    text-align: center;
    margin-bottom: 35px;
  }
  .login-form img{
    vertical-align: middle;
    margin-left:3px;
  }
  .login-form .login-btn{
    width: 100%;
    margin-bottom: 14px;
  }
  .footer{
    overflow: hidden;
  }
  .remember-me{
    display: inline-block;
    float: left;
  }
  .regist{
    display: inline-block;
    float: right;
    color: #606266;
    font-weight: 500;
    font-size: 14px;
  }
</style>
