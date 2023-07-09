<template>
  <div>
    <!--FileUpload cards-->
    <div class="row">
      <div class="col-12">
        <file-upload-card>
          <div
            class="icon-big text-center"
            :class="`icon-${fileUploadCard.type}`"
            slot="header"
          >
            <i :class="fileUploadCard.icon"></i>
          </div>
          <div class="numbers" slot="content">
            <p>{{ fileUploadCard.title }}</p>
            {{ fileUploadCard.value }}
          </div>
          <div class="fileUploadCard" slot="footer">
            <i :class="fileUploadCard.footerIcon"></i> {{ fileUploadCard.footerText }}
          </div>
        </file-upload-card>
      </div>
    </div>
    <!--Dropdown cards-->
    <div class="row">
      <div class="col"
        v-for="drops in dropdownCards"
        :key="drops.title"
      >
        <dropdown-card
            :options = drops.options
            :selected-option = drops.selectedOption
        >
<!--          <div-->
<!--            class="icon-big text-center"-->
<!--            :class="`icon-${drops.type}`"-->
<!--            slot="header"-->
<!--          >-->
<!--            <i :class="drops.icon"></i>-->
<!--          </div>-->
<!--          <div class="numbers" slot="content">-->
          <div>
            <p>{{ drops.title }}</p>
            {{ drops.value }}
          </div>
<!--          <div class="stats" slot="footer">-->
<!--            <i :class="drops.footerIcon"></i> {{ drops.footerText }}-->
<!--          </div>-->
        </dropdown-card>
      </div>
    </div>
        <!--table cards-->
        <div class="row">
        <div class="col"
             v-for="pTable in paperTables"
             :key = "pTable.title"
        >
          <card
            :title="pTable.title" :subTitle="pTable.subTitle">
            <div slot="raw-content" class="table-responsive">
              <paper-table :data="pTable.tableData" :columns="pTable.tableColumns">
              </paper-table>
            </div>
          </card>
        </div>

    </div>

<!--    &lt;!&ndash;Charts&ndash;&gt;-->
<!--    <div class="row">-->
<!--      <div class="col-12">-->
<!--        <chart-card-->
<!--          title="Users behavior"-->
<!--          sub-title="24 Hours performance"-->
<!--          :chart-data="usersChart.data"-->
<!--          :chart-options="usersChart.options"-->
<!--        >-->
<!--          <span slot="footer">-->
<!--            <i class="ti-reload"></i> Updated 3 minutes ago-->
<!--          </span>-->
<!--          <div slot="legend">-->
<!--            <i class="fa fa-circle text-info"></i> Open-->
<!--            <i class="fa fa-circle text-danger"></i> Click-->
<!--            <i class="fa fa-circle text-warning"></i> Click Second Time-->
<!--          </div>-->
<!--        </chart-card>-->
<!--      </div>-->

<!--      <div class="col-md-6 col-12">-->
<!--        <chart-card-->
<!--          title="Email Statistics"-->
<!--          sub-title="Last campaign performance"-->
<!--          :chart-data="preferencesChart.data"-->
<!--          chart-type="Pie"-->
<!--        >-->
<!--          <span slot="footer">-->
<!--            <i class="ti-timer"></i> Campaign set 2 days ago</span-->
<!--          >-->
<!--          <div slot="legend">-->
<!--            <i class="fa fa-circle text-info"></i> Open-->
<!--            <i class="fa fa-circle text-danger"></i> Bounce-->
<!--            <i class="fa fa-circle text-warning"></i> Unsubscribe-->
<!--          </div>-->
<!--        </chart-card>-->
<!--      </div>-->

<!--      <div class="col-md-6 col-12">-->
<!--        <chart-card-->
<!--          title="2015 Sales"-->
<!--          sub-title="All products including Taxes"-->
<!--          :chart-data="activityChart.data"-->
<!--          :chart-options="activityChart.options"-->
<!--        >-->
<!--          <span slot="footer">-->
<!--            <i class="ti-check"></i> Data information certified-->
<!--          </span>-->
<!--          <div slot="legend">-->
<!--            <i class="fa fa-circle text-info"></i> Tesla Model S-->
<!--            <i class="fa fa-circle text-warning"></i> BMW 5 Series-->
<!--          </div>-->
<!--        </chart-card>-->
<!--    </div>-->
  </div>
</template>
<script>
import {StatsCard, ChartCard, FileUploadCard, DropdownCard} from "@/components/index";
import Chartist from "chartist";
import { PaperTable } from "@/components";
import dropdownCard from "@/components/Cards/DropdownCard.vue";

export default {
  computed: {
    dropdownCard() {
      return DropdownCard
    },
    fileUploadCard() {
      return FileUploadCard;
    },
    paperTable(){
      return PaperTable;
    }
  },
  components: {
    DropdownCard,
    FileUploadCard,
    StatsCard,
    ChartCard,
    PaperTable,
  },
  /**
   * Chart data used to render stats, charts. Should be replaced with server data
   */
  data() {
    return {
      fileUploadCards: [
        {
          type: "warning",
          icon: "ti-upload",
          title: "Upload a file",
          value: "*",
          footerText: "Choose file",
          footerIcon: "ti-tic",
        },
      ],
      dropdownCards: [
        {
          selectedOption: 'Select Input Column',
          options: ['name','prize', 'type'],
        },
        {
          selectedOption: 'Select Weight Column',
          options: ['name','prize', 'type'],
        }
      ],
      paperTables:[
        {
          title:"Overview of the Input  File",
          subTitle: "",
          tableColumns: ["Name", "Prize", "Type"],
          tableData: [
            {
              name:"Some gene name ",
              prize:0.5,
              type: "terminal"
            },
            {
              name:"Some other gene name ",
              prize:0.7,
              type: "terminal"
            },
          ]
        }
      ],

      usersChart: {
        data: {
          labels: [
            "9:00AM",
            "12:00AM",
            "3:00PM",
            "6:00PM",
            "9:00PM",
            "12:00PM",
            "3:00AM",
            "6:00AM",
          ],
          series: [
            [287, 385, 490, 562, 594, 626, 698, 895, 952],
            [67, 152, 193, 240, 387, 435, 535, 642, 744],
            [23, 113, 67, 108, 190, 239, 307, 410, 410],
          ],
        },
        options: {
          low: 0,
          high: 1000,
          showArea: true,
          height: "245px",
          axisX: {
            showGrid: false,
          },
          lineSmooth: Chartist.Interpolation.simple({
            divisor: 3,
          }),
          showLine: true,
          showPoint: false,
        },
      },
      activityChart: {
        data: {
          labels: [
            "Jan",
            "Feb",
            "Mar",
            "Apr",
            "Mai",
            "Jun",
            "Jul",
            "Aug",
            "Sep",
            "Oct",
            "Nov",
            "Dec",
          ],
          series: [
            [542, 543, 520, 680, 653, 753, 326, 434, 568, 610, 756, 895],
            [230, 293, 380, 480, 503, 553, 600, 664, 698, 710, 736, 795],
          ],
        },
        options: {
          seriesBarDistance: 10,
          axisX: {
            showGrid: false,
          },
          height: "245px",
        },
      },
      preferencesChart: {
        data: {
          labels: ["62%", "32%", "6%"],
          series: [62, 32, 6],
        },
        options: {},
      },
    };
  },
};
</script>
<style></style>
