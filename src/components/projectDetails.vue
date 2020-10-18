<template>
  <div v-if="article != ''">
    <h2>Advanced Project Details - {{ article.toUpperCase() }}</h2>
    <div class="contentContainer" style="justify-content: flex-start">
      <div v-for="dataFields in filterInputs" :key="dataFields.id">
        <label>{{ dataFields.name }}</label>
        <input type="text" v-model="dataFields.value" />
      </div>
      <Button
        label="Submit Inputs"
        icon="pi pi-sitemap"
        iconPos="right"
        @click="submitDetails"
      />
      
    </div>
    
  </div>
</template>

<script>
import Button from "primevue/button";
export default {
  components: { Button },
  props: { article: { type: String, required: true } },
  data: function () {
    return {
      test:"",
        inputData: [
        {
          id: 0,
          articleType: "watch",
          dataToProvide: [
            { id: 0, name: "Model Name", value: null },
            { id: 1, name: "Reference Code", value: null },
            { id: 2, name: "Material Case Back", value: null },
            { id: 3, name: "Material Bezel", value: null },
            { id: 4, name: "Material Strap", value: null },
            { id: 5, name: "Material Buckle", value: null },
          ],
        },
        {
          id: 2,
          articleType: "eee",
          dataToProvide: [
            { id: 0, name: "Type of Article", value: null },
            { id: 1, name: "Country of Origin", value: null },
            { id: 2, name: "Contains Battery", value: null },
            { id: 3, name: "Reachargeable", value: null },
          ],
        },
        {
          id: 1,
          articleType: "toy",
          dataToProvide: [{ id: 0, name: "Type of Article", value: null }],
        },
        {
          id: 1,
          articleType: "leather",
          dataToProvide: [{ id: 0, name: "Type of Article", value: null }],
        },
      ],
    };
  },
  computed: {
    filterInputs: function () {
      var arr = this.inputData;
      var article = this.article;
      var filteredArray = arr.filter((input) => input.articleType === article);

      return filteredArray[0].dataToProvide;
    },

    
  },
  methods: {
      submitDetails: function () {
        this.$emit("submit-project-details",this.filterInputs)
      },
    },
};
</script>

<style scoped>
input {
  height: 3vmin;
  margin: 10px 2px 10px 2px;
  align-self: center;
  justify-self: center;
  border-radius: 3px;
  border: 2px white solid;
}

label {
  padding-left: 10px;
}
.p-button {
  width: 200px;
  justify-self: center;
  align-self: center;
  margin: auto;
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>