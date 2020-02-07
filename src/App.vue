<template>
  <div>
     <router-link :to="{path:'/xxx',query:{abc:456}}" >跳转至xxx</router-link>
     <el-button type="primary" :loading="true">加载中</el-button>
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>/