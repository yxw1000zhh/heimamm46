<template>
  
<el-dialog class="register-dialog" width="603px" center title="用户注册" :visible.sync="dialogFormVisible">
  <el-form status-icon  :model="form" :rules="rules" ref='registerForm'>
    <el-form-item  label="昵称" prop="usename" :label-width="formLabelWidth">
      <el-input v-model="form.usename" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="邮箱" prop="email" :label-width="formLabelWidth">
      <el-input v-model="form.email" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="手机" prop="phone" :label-width="formLabelWidth">
      <el-input v-model="form.phone" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="密码" prop="password" :label-width="formLabelWidth">
      <el-input show-password v-model="form.password" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="图形码" :label-width="formLabelWidth">
        <el-row>
         <el-col :span='16'>
            <el-input v-model="form.name" autocomplete="off"></el-input>
        </el-col>
           
        <el-col  :span='7' :offset='1' class="register-box">
             <img class="register-code" src="../../../assets/微信图片_20200208112147.png" alt="">
        </el-col>
        </el-row>
        
    </el-form-item>
    <el-form-item label="验证码" :label-width="formLabelWidth">
       <el-row>
         <el-col :span='16'>
            <el-input v-model="form.name" autocomplete="off"></el-input>
        </el-col>
            
        <el-col  :span='7' :offset='1'>
            <el-button >点击获取验证码</el-button>
        </el-col>
        </el-row>
    </el-form-item>
   
  </el-form>
  <div slot="footer" class="dialog-footer">
    <el-button @click="dialogFormVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
  </div>
</el-dialog>
</template>

<script>
const checkEmail=(rule,value,callback)=>{
     const reg = /\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*/
     if(reg.test(value)==true){
                callback()
            }else{
                callback(new Error('邮箱格式不对,请检查'))
            }

}
const checkPhone=(rule,value,callback)=>{
     const reg = /^(0|86|17951)?(13[0-9]|15[012356789]|166|17[3678]|18[0-9]|14[57])[0-9]{8}$/;  
     if(reg.test(value)==true){
                callback()
            }else{
                callback(new Error('手机号格式不对,请检查'))
            }
}
  export default {
    data() {
      return {
    
        dialogFormVisible: false,
        form: {
          usename: '',
          password:'',
          phone:'',
          email:''
        },
        rules:{
          username:[ {required:true,message:'用户名不能为空',trigger:'blur'},
          {min:6,max:12,message:'用户名长度为6到12位',trigger:'change'}],
          password:[ {required:true,message:'密码不能为空',trigger:'blur'},
          {min:6,max:12,message:'密码长度为6到12位',trigger:'change'}],
          email:[ {required:true,message:'密码不能为空',trigger:'blur'},
          {validator:checkEmail,trigger:'blur'}],
          phone:[ {required:true,message:'手机号不能为空',trigger:'blur'},
          {validator: checkPhone ,trigger:'blur'}]
           
         
        },
        formLabelWidth: '120px'
      };
    }
  };
</script>

<style lang='less'>
  .register-dialog{
      .el-dialog__header{
              background: linear-gradient(to right, #0dbfef,#1792f8); 
      }
      .el-dialog__header{
          color: white;
      }
      .register-box{
          height:40.8px;
      }
     .register-code{
           height:40.8px;
           width: 100%;
      }
  }
</style>