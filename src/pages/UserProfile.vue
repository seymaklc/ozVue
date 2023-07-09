<template>
  <div>
<!--  -->
<!--  <div class="row">-->
<!--    <div class="col-xl-4 col-lg-5 col-md-6">-->
<!--      <user-card> </user-card>-->
<!--      <members-card> </members-card>-->
<!--    </div>-->
<!--    <div class="col-xl-8 col-lg-7 col-md-6">-->
<!--      <edit-profile-form> </edit-profile-form>-->
<!--    </div>-->
<!--  </div>-->
  <!--FileUpload cards-->
  <div class="row">
    <div class="col-12"
    v-for="fileUpload in fileUploadCards"
         :key = "fileUpload.title"
    >
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
    <div class="col-12"
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
  </div>
</template>
<script>

import EditProfileForm from "./UserProfile/EditProfileForm.vue";
import UserCard from "./UserProfile/UserCard.vue";
import MembersCard from "./UserProfile/MembersCard.vue";
import {FileUploadCard, DropdownCard} from "@/components/index";
import { PaperTable } from "@/components";


export default {
  computed: {
    dropdownCard() {
      return DropdownCard;
    },
    fileUploadCard() {
      return FileUploadCard;
    },
    paperTable(){
      return PaperTable;
    }
  },
  components: {
    FileUploadCard,
    DropdownCard,
    EditProfileForm,
    UserCard,
    MembersCard,
    PaperTable
  },

  data() {
    return {
      fileUploadCards: [
        {
          type: "warning",
          icon: "ti-upload",
          title: "Choose a reference network file to upload",
          value: "*",
          footerText: "Choose file",
          footerIcon: "ti-tic",
        },
      ],
      dropdownCards: [
        {
          selectedOption: 'Select Column 1 *',
          options: ['Gene_1', 'Gene_2', 'Score'],
        },
        {
          selectedOption: 'Select Column 2 *',
          options: ['Gene_1', 'Gene_2', 'Score'],
        },
        {
          selectedOption: 'Select Score Column (Optional)',
          options: ['Gene_1', 'Gene_2', 'Score'],
        },
      ],

      paperTables:[
        {
          title:"Overview of the Reference Network File",
          subTitle: "",
          tableColumns: ["Column1", "Column2", "Column3"],
          tableData: [
            {
              column1:"Some gene A ",
              column2:"Some gene B",
              column3: 0.76
            },
            {
              column1:"Some gene B ",
              column2:"Some gene C",
              column3:0.73
            },
          ]
        }
      ],
    };
  },
};
</script>
<style></style>


