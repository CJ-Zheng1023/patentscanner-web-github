<template>
  <div class="app-container create-project">
    <div class="panel">
      <div class="panel-header clearfix">
        <div class="start">
          <h4 class="title">创建工程</h4>
        </div>
      </div>
      <div class="panel-body">
        <div class="form">
          <el-form :model="projectForm" :rules="rules" ref="projectForm" label-width="100px" class="demo-ruleForm">
            <el-form-item label="工程名称" prop="name">
              <el-input v-model="projectForm.name"></el-input>
            </el-form-item>
            <el-form-item label="工程描述" prop="desc">
              <el-input type="textarea" :rows="8" v-model="projectForm.desc"></el-input>
            </el-form-item>
            <el-form-item class="btn-area">
              <el-button type="primary" @click="submitForm('projectForm')">立即创建</el-button>
              <el-button @click="resetForm('projectForm')">重 置</el-button>
            </el-form-item>
          </el-form>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        projectForm:{
          name: '',
          desc:''
        },
        rules: {
          name: [
            { required: true, message: '请输入工程名称', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>
<style scoped lang="scss">
  .form{
    width:900px;
    margin:40px auto;
  }
  .create-project .btn-area{
    text-align: center;
  }
</style>
