<template>
  <el-main>
    <el-table :data="tableData" height="800" style="width: 100%" stripe>
      <el-table-column
        prop="PROJECT_DATE"
        label="Date"
        :formatter="formatterTime"
        width="180"
      />
      <el-table-column
        prop="PROJECT_FUNDS"
        label="课题经费（万）"
        width="180"
      />
      <el-table-column prop="PROJECT_GOVERNMENT" label="发布单位" width="" />
      <el-table-column prop="PROJECT_NAME" label="课题名称" />
    </el-table>
  </el-main>
</template>

<script>
export default {
  name: "ProjectTable",
  data() {
    return {
      count: 5,
      tableData: [],
    };
  },
  methods: {
    filterGov(value, row) {
      return row.PROJECT_GOVERNMENT.includes(value);
    },
    formatterTime(row) {
      let x = new Date(row.PROJECT_DATE * 1000);
      return x.toLocaleDateString();
    },
  },
  mounted() {
    this.$http
      .post(
        "https://keyanpro.com/api/demo/ProjectGov/list",
        {
          release_time_seven: "",
          pro_id: "",
          project_industry_id: "",
          release_time_thirty: "",
          type_id: "",
          project_status_end: "",
          project_status: "",
          help_money_start: "",
          help_money_end: "",
          limit: 50,
          page: 1,
          title: "",
        },
        {}
      )
      .then((response) => {
        console.log(response);
        this.tableData = response["data"]["data"]["data"];

        // let demoData = response["data"]["data"]["data"];
        // console.log(demoData);
      });
  },
};
</script>

<style></style>
