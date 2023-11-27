<template>
<v-dialog
      v-model="dialog"
      width="auto"
    >
      <v-card>
        <v-card-text>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
        </v-card-text>
        <v-card-actions>
          <v-btn @click="dialog = false">Close Dialog</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>
  
<script>
  export default {
    name: "ProductDialog",
    data() {
      return {
        dialog: false,
      };
    },
    methods: {
    }
  };
</script>
  
<style>
  /* Add your CSS styles here */

</style>