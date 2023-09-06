<template>
    <div style="padding: 10px">
      <el-button type="primary">Add data</el-button>
    </div>

    <div style="margin: 10px  0">
      <el-table :data="tableData" style="width: 100%">
        <el-table-column prop="date" label="Date" width="180" align = "center" />
        <el-table-column prop="name" label="Name" width="180" align = "center"/>
        <el-table-column prop="address" label="Address" />
      </el-table>
    </div>
</template>

<script setup>
const tableData = [
  {
    date: '2016-05-03',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-02',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-04',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  }]
</script>

<style>
.home {
  color: red;
}
</style>

