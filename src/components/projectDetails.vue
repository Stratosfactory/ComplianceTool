<template>
  <div>

    

    <div>{{ article }}</div>
    
      
    
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
          inputFields: [
            "Project Name",
            "Reference Code",
            "Material Case Back",
            "Material Bezel",
            "Meterial Strap",
            "Material Buckle",
          ],
        },
        {
          id: 1,
          articleType: "eee",
          inputsFields: [
            "Project Name",
            "Contains Batteries?",
            "Sourced From",
            "Wattage",
          ],
        },
      ],
      
    };
  },
};
</script>

<style>
</style>