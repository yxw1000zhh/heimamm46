<template>
  <div class='login-container'>
      <div class="left-box">
        <img src="'../../assets/9.png" class="logo"><img>
        <span class="title">黑马面面</span>
        <span class="line"></span>
        <span class="sub-title">用户登录</span>
      </div>
      <img src="../../assets/login_banner_ele.png" alt="">

  </div>

</template>

<script>
export default {
 name:'login'
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
     .title-box {
       display: flex;
       align-items: center;
       margin-top: 44px;
       margin-left: 48px;
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
 }
 }
 
</style>