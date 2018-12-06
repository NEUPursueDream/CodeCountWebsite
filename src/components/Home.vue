<template>
  <div class="Home">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>{{msg}}</el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>
  </div>
</template>

<script>
  export default {
    name: "Home",
    data() {
      return {
        msg: "If you see this page, it means system get service data faild!"
      };
    },
    created() {
      this.getHelloMsg();
    },
    methods: {
      getHelloMsg() {
        this.$http.get("http://localhost:8080/hello/vue").then((response) => { //成功的回调
          this.msg = response.bodyText;
          this.$notify({
            title: '成功',
            message: '获取后台接口消息成功',
            type: 'success'
          });
        }).catch((response) => { //失败的回调
          this.$notify.error({
            title: '失败',
            message: '获取后台接口消息失败'
          });
        });
      }
    }
  };

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .el-header,
  .el-footer {
    background-color: #b3c0d1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }

  .el-aside {
    background-color: #d3dce6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }

  .el-main {
    background-color: #e9eef3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }

  body>.el-container {
    margin-bottom: 40px;
  }

  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }

  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }

</style>
