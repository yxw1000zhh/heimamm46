<template>
  <div>我是xxx组件</div>
</template>
<script>
export default {
  created() {
    //   route :只是取当条路由的基本信息
    window.console.log(this.$route.query.abc);
  }
};
</script>
<style>
</style>