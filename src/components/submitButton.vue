<template>
  <div class="contentContainer" style="margin: 40px auto 40px auto">
    <Button label="Projekt abspeichern" icon="pi pi-check" iconPos="right" @click="submitToDatabase" />
  </div>
</template>

<script>
import Button from "primevue/button";

export default {
  props: {
    projectBasics: { type: Object, required: true },
    projectAdvanced: { type: Array, required: true },
    selectedArticle: { type: String, required: true },
  },
  components: { Button },
  methods: {
    submitToDatabase: function () {
      fetch("https://complianceapp-test-9ff9b.firebaseio.com/projects.json",{
          method:"POST",
          headers:{
              "Content-Type":"application/json"
          },
          body: JSON.stringify({
              article:this.selectedArticle,
              projectBasics:this.projectBasics,
              projectAdvanced:this.projectAdvanced,
          }),

      }
      
      );
    },
  },
};
</script>

<style scoped>
div Button {
  margin: 10px auto 10px auto;
}
</style>