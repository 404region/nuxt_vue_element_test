<template>
  <div>
    <NavVue/>
    <h1>Администрирование</h1>
    <el-row>
      <el-col :span="16"><div class="grid-content bg-purple">
        <h2>Пользователи</h2>
        <DataTableUsers/>
      </div></el-col>
      <el-col :span="8"><div class="grid-content bg-purple">
        <h2>События</h2>
        <DateTableEvents/>
      </div></el-col>
    </el-row>
  </div>
</template>

<script>
  import DataTableUsers from '../components/DataTableUsers.vue';
  import DateTableEvents from '../components/DateTableEvents.vue';

  export default {
      name: "IndexPage",
      components: { DataTableUsers, DateTableEvents },
  }
</script>

<style>
  .el-row {
    margin-bottom: 20px;
    &:last-child {
      margin-bottom: 0;
    }
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
</style>