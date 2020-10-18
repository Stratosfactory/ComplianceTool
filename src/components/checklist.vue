<template>
  <div v-if="projectAdvanced!=null">
      <h2>Compliance Checklist</h2>
       <div class="headerBasic">
        
            <div v-for="(item, index) in projectBasics" :key="index" class="headerElement"> <span>{{index}}: </span>{{item}}</div>
        
    </div>

    <div class="headerBasic">
        
            <div v-for="(item, index) in projectAdvanced" :key="index" class="headerElement"> <span>{{item.name}}:</span> {{item.value}}</div>
        
    </div>

    
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
    border: 2px black solid;
    margin-bottom: 10px;

}
.headerElement{
    width: 49.5%;
    border: 2px hsl(200, 30%, 30%) solid;
    margin: 1px 1px 1px 1px;
    background-color:hsl(200, 30%, 30%) ;
    color:white;
    
}
span{
    color: lightgrey
}
</style>