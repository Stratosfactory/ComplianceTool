<template>
  <div v-if="projectAdvanced != null">
    <h2>Compliance Checklist</h2>
    <div class="headerBasic">
      <div
        v-for="(item, index) in projectBasics"
        :key="index"
        class="headerElement"
      >
        <span>{{ index }}: </span>{{ item }}
      </div>
      <div id="preview" class="headerElement">
        <span>Project Image: </span> <br /><img
          :src="projectImage"
          v-if="projectImage != null"
        />
      </div>
    </div>

    <div class="headerBasic">
      <div
        v-for="(item, index) in projectAdvanced"
        :key="index"
        class="headerElement"
      >
        <span>{{ item.name }}:</span> {{ item.value }}
      </div>
    </div>
    <div class="checklist">
      <DataTable :value="filterRuleSet.ruleSet" class="table" >
        <Column field="category" header="Category" headerClass="tableHeader" bodyClass="rowElement"></Column>
        <Column field="rule" header="Rule Name" headerClass="tableHeader" bodyClass="rowElement"></Column>
        <Column field="ruleExp" header="Explanation" headerClass="tableHeader" bodyClass="rowElement"></Column>
      </DataTable>
    </div>
  </div>
</template>

<script>
import DataTable from "primevue/datatable";
import Column from "primevue/column";
import ruleSet from "./Rulesets/ruleset.json";
export default {
  components: { DataTable, Column },
  props: {
    projectBasics: { type: Object, required: true },
    projectAdvanced: { type: Array, required: true },
    selectedArticle: { type: String, required: true },
    projectImage: { type: String },
  },
  data: function () {
    return {
      ruleSet: ruleSet,
    };
  },
  computed: {
    filterRuleSet: function () {
      var article = this.selectedArticle;
      const filteredRule = this.ruleSet.filter(
        (input) => input.articleType === article
      );
      return filteredRule[0];
    },
  },
};
</script>

<style scoped>
.headerBasic {
  display: flex;
  align-items: stretch;
  align-content: space-around;
  justify-content: space-evenly;
  width: 70%;
  margin: auto;
  flex-wrap: wrap;
  flex-direction: row;
  border: 2px black solid;
  margin-bottom: 10px;
}
.headerElement {
  width: 49.5%;
  border: 2px hsl(200, 30%, 30%) solid;
  margin: 1px 1px 1px 1px;
  background-color: hsl(200, 30%, 30%);
  color: white;
}
span {
  color: lightgrey;
}
img {
  width: 200px;
  height: 200px;
}
.checklist {
  width: 70%;
  margin: auto;
  margin-top: 20px;
}
.table {
  border: 2px hsl(200, 30%, 30%) solid;
}
</style>

<style>
.tableHeader {
  background-color: hsl(200, 30%, 30%) !important;
  color:white !important;
  font-family: "Sora", sans-serif;
  border:white solid 2px !important;
  
}

.rowElement{
  border-right:1px hsl(200, 30%, 30%) solid !important;
}

</style>