<template>
  <div style="padding: 10px">
    <el-button type="primary" @click="dialogFormVisible = true"
      >Add data</el-button
    >
  </div>

  <div style="margin: 10px 0">
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="date" label="Date" width="180" align="center" />
      <el-table-column prop="name" label="Name" width="180" align="center" />
      <el-table-column prop="address" label="Address" />
    </el-table>
  </div>

  <el-dialog v-model="dialogFormVisible" title="informations personelles">
    <el-form :model="form" label-width="120px">
      <el-form-item label="Date">
        <el-input v-model="form.date" autocomplete="off" />
      </el-form-item>

      <el-form-item label="Name">
        <el-input v-model="form.date" autocomplete="off" />
      </el-form-item>

      <el-form-item label="Address">
        <el-input v-model="form.address" autocomplete="off" />
      </el-form-item>
    </el-form>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="dialogFormVisible = false">Cancel</el-button>
        <el-button type="primary" @click="dialogFormVisible = false">
          Confirm
        </el-button>
      </span>
    </template>
  </el-dialog>
</template>

<script setup>
import { ref, reactive } from "vue";

const tableData = [
  {
    date: "2016-05-03",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-02",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-04",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
];

const form = reactive({
});

const dialogFormVisible = ref(false);
</script>

<style>
.home {
  color: red;
}
</style>

