<template>
  <el-main>
    <el-table
      :data="tableData"
      height="57em"
      style="width: 100%"
      stripe
      v-loading="loading"
    >
      <el-table-column label="课题名称">
        <template #default="props">
          <a v-bind:href="props.row.PROJECT_URL" target="_blank">{{
            props.row.PROJECT_NAME
          }}</a>
        </template>
      </el-table-column>
      <el-table-column
        prop="PROJECT_GOVERNMENT"
        label="发布单位"
        width=""
        :filters="[
          { text: '国家级', value: '国家' },
          { text: '广东省级', value: '广东' },
          { text: '深圳市级', value: '深圳' },
        ]"
        :filter-method="filterGov"
      />
      <el-table-column
        prop="PROJECT_FUNDS"
        label="课题经费（万）"
        sortable
        :sort-method="sortFunding"
        :filters="[{ text: '大于 10 万', value: 10 }]"
        :filter-method="filterFunding"
        width="180"
      />
      <el-table-column
        prop="PROJECT_DATE"
        label="发布时间"
        :formatter="formatterTime"
        sortable
        width="180"
      />
      <el-table-column
        prop="PROJECT_DATE_END"
        label="截止时间"
        :formatter="formatterEndTime"
        sortable
        width="180"
      />
      <el-table-column type="expand">
        <template #default="props">
          {{ props.row.PROJECT_CONTENT }}
        </template>
      </el-table-column>
    </el-table>
    <p></p>
    <el-button
      round
      v-on:click="loadData"
      v-loading="loading"
      type="primary"
      plain
      >加载更多</el-button
    >
  </el-main>
</template>

<script>
export default {
  name: "ProjectTable",
  data() {
    return {
      pageIndex: 0,
      tableData: [],
      loading: false,
    };
  },
  methods: {
    loadData() {
      this.loading = true;
      this.pageIndex = this.pageIndex + 1;
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
            page: this.pageIndex,
            title: "",
          },
          {}
        )
        .then((response) => {
          // console.log(response);
          this.tableData = this.tableData.concat(
            response["data"]["data"]["data"]
          );
          this.loading = false;
        });
    },
    filterGov(value, row) {
      return row.PROJECT_GOVERNMENT.includes(value);
    },
    filterFunding(value, row) {
      return row.PROJECT_FUNDS > value;
    },
    formatterTime(row) {
      let x = new Date(row.PROJECT_DATE * 1000);
      return x.toLocaleDateString();
    },
    formatterEndTime(row) {
      let x = new Date(row.PROJECT_DATE_END * 1000);
      return x.toLocaleDateString();
    },
    sortFunding(a, b, type) {
      if (type == "asc") {
        return Number(a.PROJECT_FUNDS) > Number(b.PROJECT_FUNDS) ? -1 : 1;
      } else {
        return Number(a.PROJECT_FUNDS) > Number(b.PROJECT_FUNDS) ? 1 : -1;
      }
    },
  },
  mounted() {
    this.loadData();
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
