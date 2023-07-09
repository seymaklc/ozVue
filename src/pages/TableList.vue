<template>
  <div class="row">
    <div class="col-12">
      <card :title="table1.title" :subTitle="table1.subTitle">
        <div slot="raw-content" class="table-responsive">
          <paper-table :data="table1.data" :columns="table1.columns">
          </paper-table>
        </div>
      </card>
    </div>

    <div class="col-12">
      <card class="card-plain">
        <div class="table-full-width table-responsive">
          <paper-table
            type="hover"
            :title="table2.title"
            :sub-title="table2.subTitle"
            :data="table2.data"
            :columns="table2.columns"
          >
          </paper-table>
        </div>
      </card>
    </div>
  </div>
</template>

<script>
import { PaperTable } from "@/components";

let col1 = "col1";
let col2 = "col2";
let col3 = "col3";

let tableColumns = [col1, col2, col3];
//const tableColumns = ["col1", "col2", "col3"];
const tableData = [
  {
    col1: 1,
    col2: "Dakota Rice",
    col3: "$36.738",
  },
  {
    col1: 2,
    col2: "Minerva Hooper",
    col3: "$23,789",
  },
  {
    col1: 3,
    col2: "Sage Rodriguez",
    col3: "$56,142",
  },
  {
    col1: 4,
    col2: "Philip Chaney",
    col3: "$38,735",
  },
];

export default {
  components: {
    PaperTable,
  },
  props:{
    tableColumns:[col1, col2, col3],
    tableData:[
      {
        col1: 1,
        col2: "Dakota Rice",
        col3: "$36.738",
      },
      {
        col1: 2,
        col2: "Minerva Hooper",
        col3: "$23,789",
      },
      {
        col1: 3,
        col2: "Sage Rodriguez",
        col3: "$56,142",
      },
      {
        col1: 4,
        col2: "Philip Chaney",
        col3: "$38,735",
      }]
  },

  data() {
    return {
      table1: {
        title: "Stripped Table",
        subTitle: "Here is a subtitle for this table",
        columns: [...this.props.tableColumns],
        data: [...this.props.tableData],
      },
      table2: {
        title: "Table on Plain Background",
        subTitle: "Here is a subtitle for this table",
        columns: [...this.props.tableColumns],
        data: [...this.props.tableData],
      },
    };
  },
};
</script>
<style></style>
