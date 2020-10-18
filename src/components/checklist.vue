<template>
  <div v-if="projectAdvanced!=null">
      <h2>Compliance Checklist</h2>
       <div class="headerBasic">
        
            <div v-for="(item, index) in projectBasics" :key="index" class="headerElement">{{index}}: {{item}}</div>
        
    </div>
    <div>{{projectAdvanced}}</div>
   <!-- <div>{{ ruleSet }}}</div> -->
  </div>
</template>

<script>
import ruleSet from "./Rulesets/ruleset.json"
export default {
    props:{projectBasics:{type:Object, required:true},projectAdvanced:{type:Array,required:true},selectedArticle:{type:String,required:true}},
    data: function(){
        return{
           ruleSet:ruleSet,

        }
    }
}
</script>

<style scoped>
.headerBasic{
    display: flex;
    align-items:stretch;
    align-content: space-around;
    justify-content: space-evenly;
    width: 70%;
    margin: auto;
    flex-wrap: wrap;
    flex-direction:row;

}
.headerElement{
    width: 49.5%;
    border: 2px hsl(200, 30%, 30%) solid;
    margin: 1px 1px 1px 1px;
}
</style>