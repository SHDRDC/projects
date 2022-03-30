<template>
  <div v-show="show">
    <el-table :data="tableData" style="width: 100%" height="37em" stripe>
      <el-table-column type="index" label="序号" width="100"> </el-table-column>
      <!-- <el-table-column prop="index" label="序号" width="180" /> -->
      <el-table-column label="奖项">
        <template #default="props">
          <a v-bind:href="props.row.link" target="_blank">{{
            props.row.name
          }}</a>
        </template>
      </el-table-column>
      <el-table-column prop="date" label="通知时间" />
      <el-table-column prop="class" label="类别" />
    </el-table>
    <p></p>
    <p>
      重点参考：<a href="./demo.pdf" target="_blank"
        >南方科技大学科研奖励申报手册</a
      >
    </p>
  </div>
</template>

<script>
export default {
  name: "AwardTable",
  props: {
    show: Boolean,
  },
  data() {
    return {
      tableData: [
        {
          name: "国家科学技术奖",
          date: "11 月",
          class: "自然科学",
          link: "http://www.most.gov.cn/tztg/?searchword=%E6%8F%90%E5%90%8D&prepage=10&channelid=44374&sortfield=-DOCRELTIME&strKeyWords=&itime=0",
        },
        {
          name: "广东省科学技术奖",
          date: "9 月",
          class: "自然科学",
          link: "http://gdstc.gd.gov.cn/zwgk_n/tzgg/index_10.html",
        },
        {
          name: "广东省社会科学优秀成果奖",
          date: "按通知",
          class: "社会科学",
          link: "http://www.gdskl.com.cn/index_news_396.shtml",
        },
        {
          name: "中华医学科技奖",
          date: "2-3 月",
          class: "医学",
          link: "https://www.cma.org.cn/col/col4224/index.html",
        },
        {
          name: "中华预防医学会科学技术奖",
          date: "1-3 月",
          class: "医学",
          link: "http://www.cpma.org.cn/zhyfyxh/tzgg/new_list.shtml",
        },
        {
          name: "深圳市科学技术奖",
          date: "1-3 月",
          class: "自然科学",
          link: "http://stic.sz.gov.cn/xxgk/tzgg/index.html",
        },
        {
          name: "深圳市国家和广东省科学技术奖配套奖励",
          date: "4 月",
          class: "自然科学",
          link: "http://stic.sz.gov.cn/xxgk/tzgg/index.html",
        },
        {
          name: "深圳市哲学社会科学优秀成果奖",
          date: "按通知",
          class: "社会科学",
          link: "http://www.szass.com/xxgk/tzgg/index.html",
        },
        {
          name: "深圳标准领域专项资金",
          date: "3 月（2021）",
          class: "专项资金",
          link: "http://amr.sz.gov.cn/xxgk/qt/tzgg/index.html",
        },
      ],
    };
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
