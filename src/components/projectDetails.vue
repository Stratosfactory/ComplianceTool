<template>
  <div v-if="article != ''">
    <h2>Advanced Project Details - {{ article.toUpperCase() }}</h2>
    <div class="contentContainer" style="justify-content: flex-start">
      <div v-for="dataFields in filterInputs" :key="dataFields.id">
        <label>{{ dataFields.name }}</label>
        <component
          :is="dataFields.type"
          v-model="dataFields.value"
          :options="dataFields.options"
        ></component>
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
import InputText from "primevue/inputtext";
import Dropdown from "primevue/dropdown";
export default {
  components: { Button, Dropdown, InputText },
  props: { article: { type: String, required: true } },
  data: function () {
    return {
      test: "",
      inputData: [
        {
          id: 0,
          articleType: "watch",
          dataToProvide: [
            {
              id: 0,
              name: "Modelname",
              type: "InputText",
              value: null,
              options: null,
            },
            {
              id: 1,
              name: "Referenz",
              type: "InputText",
              value: null,
              options: null,
            },
            {
              id: 2,
              name: "Material Gehäuse",
              type: "Dropdown",
              value: null,
              options: ["Gold", "Platin", "Silber"],
            },
            {
              id: 3,
              name: "Material Lünette",
              type: "Dropdown",
              value: null,
              options: ["A", "B", "C"],
            },
            {
              id: 4,
              name: "Material Band",
              type: "Dropdown",
              value: null,
              options: ["Leder", "Croco", "Stoff"],
            },
            {
              id: 5,
              name: "Material Schliesse",
              type: "Dropdown",
              value: null,
              options: ["Gold", "Silber", "Platin"],
            },
          ],
        },
        {
          id: 2,
          articleType: "eee",
          dataToProvide: [
            {
              id: 0,
              name: "Artikelbezeichnung",
              type: "InputText",
              value: null,
              options: null,
            },
            {
              id: 1,
              name: "Herkunftsland",
              type: "InputText",
              value: null,
              options: null,
            },
            {
              id: 2,
              name: "Enthält Batterien",
              type: "Dropdown",
              value: null,
              options: ["JA", "NEIN"],
            },
            {
              id: 3,
              name: "Wiederaufladbar",
              type: "Dropdown",
              value: null,
              options: ["JA", "NEIN"],
            },
          ],
        },
        {
          id: 1,
          articleType: "toy",
          dataToProvide: [{
              id: 0,
              name: "Artikelbezeichnung",
              type: "InputText",
              value: null,
              options: null,
            },],
        },
        {
          id: 1,
          articleType: "leather",
          dataToProvide: [{
              id: 0,
              name: "Artikelbezeichnung",
              type: "InputText",
              value: null,
              options: null,
            },],
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
      this.$emit("submit-project-details", this.filterInputs);
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