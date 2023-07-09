 <template>
   <card>
    <div class="dropdown-card">
      <div class="dropdown-header" @click="toggleDropdown">
        <span class="dropdown-title">{{ selectedOption }}</span>
        <i :class="{'fa-chevron-up': isOpen, 'fa-chevron-down': !isOpen}" class="fa"></i>
      </div>
      <ul v-show="isOpen" class="dropdown-list">
        <li v-for="(option, index) in options" :key="index" @click="selectOption(option)">
          {{ option }}
        </li>
      </ul>
    </div>
   </card>
  </template>

<script>
export default {
  name: "DropdownCard",
  props:{
    isOpen: false,
    selectedOption: 'Select an option',
    options: ["name", "prize", "type"]
  },

  data() {
    return {
      isOpen: this.props.isOpen,
      selectedOption: this.props.selectedOption,
      options: this.props.options
    };
  },
  methods: {
    toggleDropdown() {
      this.isOpen = !this.isOpen;
    },
    selectOption(option) {
      this.selectedOption = option;
      this.isOpen = false;
    },
  },
};
</script>

 <style scoped>
 .dropdown-card {
   position: relative;
 }

 .dropdown-header {
   display: flex;
   align-items: center;
   justify-content: space-between;

   background-color: #f2f2f2;
   cursor: pointer;
 }

 .dropdown-title {
 }

 .dropdown-list {
   position: center;
   top: 100%;
   left: 0;
   width: 100%;
   list-style-type: none;
   padding: 0;
   margin: 0;
   background-color: #fff;
   border: 1px solid #ccc;
   box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
 }

 .dropdown-list li {
   padding: 10px;
   cursor: pointer;
 }

 .dropdown-list li:hover {
   background-color: #f2f2f2;
 }

 .fa {
   font-size: 12px;
   transition: transform 0.3s;
 }

 .fa-chevron-up {
   transform: rotate(-180deg);
 }

 .fa-chevron-down {
   transform: rotate(0deg);
 }
 </style>
