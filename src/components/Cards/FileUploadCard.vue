<template>
  <card>
    <div>
      <div class="row">
        <div class="col-5" v-if="$slots.header">
          <slot name="header"></slot>
        </div>
        <div class="col-7" v-if="$slots.content">
          <input type="file" ref="fileInput1" @change="handleFileChange" />
          <button @click="uploadFile(1)">Upload</button>
          <slot name="content">
          </slot>
        </div>
      </div>
      <div v-if="$slots.footer">
        <hr />
        <slot name="footer"></slot>
      </div>
    </div>
  </card>
</template>

<script>
import Card from "./Card.vue";
export default {
  name: "file-upload-card",
  components: {
    Card,
  },
  methods: {
    handleFileChange(event) {
      const file = event.target.files[0];
      // Process the file as needed (e.g., upload to a server, store in local state)
      console.log('Selected file:', file);
    },
    uploadFile(tabNumber) {
      // You can handle file upload logic here based on the tab number
      // For example, you can use conditionals or a switch statement
      if (tabNumber === 1) {
        // File upload logic for the first tab
        // const file = this.$refs.fileInput1.files[0];
        // ...
      } else if (tabNumber === 2) {
        // File upload logic for the second tab
        // const file = this.$refs.fileInput2.files[0];
        // ...
      }
    },
  }
}
</script>

<style scoped>

</style>
