<template>
  <div v-if="article != ''">
    <h2>Advanced Project Details - {{ article.toUpperCase() }}</h2>
    <div class="contentContainer">
      <div v-for="input in inputData" :key="input.id">
        <div v-for="dataFields in input.dataToProvide" :key="dataFields.id">
          <label>{{dataFields.name}}</label> <input type="text" v-model="dataFields.value">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: { article: { type: String, required: true } },
  data: function () {
    return {
      inputData: [
        {
          id: 0,
          articleType: "watch",
          dataToProvide: [
            { id: 0, name: "Model Name", "value":null },
            { id: 1, name: "Reference Code", "value":null },
            { id: 2, name: "Material Case Back", "value":null },
            { id: 3, name: "Material Bezel", "value":null },
            { id: 4, name: "Material Strap", "value":null },
            { id: 5,name: "Material Buckle", "value":null },
          ],
        },
        
      ],
    };
  },
};
</script>

<style>
</style>