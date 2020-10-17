<template>
  <div v-if="article != ''">
    <h2>Advanced Project Details - {{ article.toUpperCase() }}</h2>
    <div class="contentContainer">
      
        <div v-for="dataFields in filterInputs" :key="dataFields.id">
          <label>{{dataFields.name}}</label> <input type="text" v-model="dataFields.value">
          
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
        {
          id: 1,
          articleType: "eee",
          dataToProvide: [
            { id: 0, name: "Type of Article", "value":null },
            { id: 1, name: "Country of Origin", "value":null },
            { id: 2, name: "Contains Battery", "value":null },
            { id: 3, name: "Reachargeable", "value":null },
            
          ],
        },
      ],
    };
  },
  computed:{
   filterInputs:function(){
     var arr=this.inputData
     var article=this.article
     var filteredArray = arr.filter(input => input.articleType === article);
    
     return filteredArray[0].dataToProvide;
   }}
};
</script>

<style>
</style>