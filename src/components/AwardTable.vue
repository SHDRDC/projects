<template>
  <el-table :data="tableData" style="width: 100%">
    <el-table-column prop="name" label="Name" width="180" />
    <el-table-column prop="date" label="Date" width="180" />
    <el-table-column prop="address" label="Address" />
  </el-table>
</template>

<script>
export default {
  name: "AwardTable",
  data() {
    return { tableData: [{ name: "a", date: "b", address: "c" }] };
  },
};
</script>

<style>
.el-table__expanded-cell {
  white-space: pre-line;
  color: #ff8700;
}

a:link {
  text-decoration: none;
  color: #32b17a;
}
</style>
