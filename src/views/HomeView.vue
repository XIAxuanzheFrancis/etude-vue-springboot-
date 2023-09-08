<template>
  <div style="padding: 10px">
    <el-input style="width: 300px" placeholder="Please enter a name" v-model="name" clearable></el-input>
    <el-button type="primary" @click="search" style ="margin-left: 5px; margin-right: 1px">Search</el-button>
    <el-button type="primary" @click="HandleAdd">Add data</el-button>
  </div>

  <div style="margin: 10px 0">
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="date" label="Date" width="180" align="center" />
      <el-table-column prop="name" label="Name" width="180" align="center" />
      <el-table-column prop="address" label="Address" width="180" align="center"/>
      <el-table-column label="Action" width="180" align="center">
       <template #default="scope">
        <el-button link type="primary" size="small" @click="handleEdit(scope.row, scope.$index)">Edit</el-button>
        <el-button link type="danger" size="small" @click.prevent="deleteRow(scope.$index)">Delete</el-button>
      </template>
      </el-table-column>
    </el-table>
  </div>

  <el-dialog v-model="dialogFormVisible" title="informations personelles" width = "40%">
    <el-form :model="form" label-width="120px" style="padding-right: 50px">
      <el-form-item label="Date">
        <el-input v-model="form.date" autocomplete="off" />
      </el-form-item>

      <el-form-item label="Name">
        <el-input v-model="form.name" autocomplete="off" />
      </el-form-item>

      <el-form-item label="Address">
        <el-input v-model="form.address" autocomplete="off" />
      </el-form-item>
    </el-form>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="dialogFormVisible = false">Cancel</el-button>
        <el-button type="primary" @click="save">
          Confirm
        </el-button>
      </span>
    </template>
  </el-dialog>
</template>

<script setup>
import { ref, reactive } from "vue";

const tableData = reactive([
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
]);

let form = reactive({})
const globalIndex = ref(-1)
const dialogFormVisible = ref(false)
const name = ref('')

const save = () => {
  if(globalIndex.value>=0){
    tableData[globalIndex.value] = form
    globalIndex.value = -1
  }else{
    tableData.push(form);
  }
  dialogFormVisible.value = false
}

const HandleAdd = () => {
  form = reactive({});
  dialogFormVisible.value = true
}

const deleteRow = (index) => {
tableData.splice(index,1)
}

const handleEdit = (row, index) => {  
  const newObj = Object.assign({},row)
  form = reactive(newObj)
  globalIndex.value = index
  dialogFormVisible.value = true
}

const search = () => {
  const filteredData = tableData.filter(v => v.name.includes(name.value))
  tableData.length = 0
  tableData.push(...filteredData)
}

</script>

<style>
.home {
  color: red;
}
</style>

