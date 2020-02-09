<template>
  <div class='login-container'>
      <div class="left-box">
        <div class="title-box">
          <img src="../../assets/9.png" alt="">
        <span class="title">黑马面面</span>
        <span class="line"></span>
        <span class="sub-title">用户登录</span>
        </div>
      
      <!-- 表单 -->
      <el-form ref="loginForm" :rules='rules' :model="loginForm" label-width="43px">
  <el-form-item >
    <el-input prefix-icon="el-icon-user" placeholder="请输入手机号" v-model="loginForm.phone"></el-input>
  </el-form-item >
  <el-form-item prop='password'>
    <el-input prefix-icon="el-icon-lock" placeholder="请输入密码" v-model="loginForm.password"></el-input>
  </el-form-item>
  <!-- 验证码 -->
  <el-form-item prop='loginCode'>
    <el-row>
      <el-col :span="17">
       <el-input prefix-icon="el-icon-key" placeholder="请输入验证码" v-model="loginForm.loginCode"></el-input>
      </el-col>
      <el-col :span="7">
        <img class="login-code" src="../../assets/微信图片_20200208112147.png" alt="">
      </el-col>
    </el-row>
    
  </el-form-item>
  <el-form-item >
    <el-checkbox v-model="loginForm.isChecked">我已阅读并同意
      <el-link type='primary'>用户协议</el-link>
      和
      <el-link type='primary'>隐私条款</el-link>
    </el-checkbox>
  </el-form-item>
  <el-form-item >
   <el-button class="my-btn" type="primary" @click="submitForm('loginForm')">登陆</el-button>
   <el-button @click="showRegister" class="my-btn" type="primary">注册</el-button>
   
  </el-form-item>
 
</el-form>
</div>
      <img src="../../assets/login_banner_ele.png" alt="">
<!-- 托管软件应用 -->
<reisterDialog ref='registerDialog'></reisterDialog>
  </div>

</template>

<script>
import reisterDialog from './components/registerDialog'
export default {
 name:'login',
 components:{
  reisterDialog
 },
 data() {
   return {
     loginForm:{
       phone:'',
       password:'',
       loginCode:'',
       isChecked:false
     },
     rules:{
       password:[
         {required: true,message:'密码不能为空',trigger:'blur'},
         {min:6,max:12,message:'密码长度为6-12位',trigger:'blur'}
       ],
      loginCode:[
         {required:true,message:'验证码不能为空',trigger:'blur'},
           {min:6,max:12,message:'yanz长度为4位',trigger:'blur'}
       ],
     }
   }
 },
 methods: {
   submitForm(formName){
    this.$refs[formName].validate(valid=>{
      if (valid) {
        this.$message.success('验证成功')
      }else{
        this.$message.error('验证失败');
        return false;
      }
    })
   },
   showRegister(){
     this.$refs.registerDialog.dialogFormVisible=true;
   }
 },
}
</script>

<style lang='less'>
 .login-container {
     height: 100%;
    background:linear-gradient(225deg,rgba(20,147,250,1),rgba(1,198,250,1));
    display: flex;
    align-items: center;
    justify-content: space-around;
    .left-box{
    width: 478px;
    background-color: #f5f5f5;
    height: 550px;
    padding-right: 41px;
    box-sizing: border-box;
     .title-box {
       display: flex;
       align-items: center;
       margin-top: 44px;
       margin-left: 48px;
       margin-bottom: 27px;
       .title{
         font-size: 24px;
         margin-left: 16px;
         margin-right: 14px;
       }
       .line{
         width: 1px;
         height: 28px;
         background-color: #C7C7C7;
       }
       .sub-title{
         font-size: 21px;
         margin-left: 12px;
       }
     }
     .login-code{
       width: 100%;
       height: 40.8px;
     }
      .my-btn{
        width: 100%;
       margin-left:0px;
       margin-bottom: 26px;
         
      }
    
 }
 .el-checkbox{
   display: flex;
   .el-checkbox__label{
     display: flex;
   }
 }
 }
 
</style>